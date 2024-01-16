# Fast ResNet on CIFAR-10

<hr>

## Contents

1. [Highlights](#Highlights)
2. [Requirements](#Requirements)
3. [Usage](#Usage)
4. [Results](#Results)


<hr>

## Highlights
The goal of this project is to create a slightly modified version of the fast ResNet model from David Page's amazing blog post [How to Train Your ResNet 8: Bag of Tricks](https://myrtle.ai/learn/how-to-train-your-resnet-8-bag-of-tricks/), where a modified ResNet is trained to reach 94% accuracy in 26 seconds on a V100 GPU. Our model trained for 23 minutes on a single A100 GPU for 50 epochs and reached a final accuracy of 95% on `CIFAR-10`.

<hr>

## Requirements
```shell
pip install -r requirements.txt
```

<hr>

## Usage
To replicate the reported results, clone this repo
```shell
cd your_directory git@github.com:jordandeklerk/Fast-ResNet.git
```
and run the main training script
```shell
python train.py 
```
Make sure to adjust the checkpoint directory in train.py to store checkpoint files.

<hr>

## Results
We test our approach on the `CIFAR-10` dataset with the intention to extend our model to 4 other small low resolution datasets: `Tiny-Imagenet`, `CIFAR100`, `CINIC10` and `SVHN`. All training took place on a single A100 GPU.
  * CIFAR10
    * ```fast_resnet_cifar10_input32``` - 94.9 @ 32

Flop analysis:
```
total flops: 1515005952
total activations: 753674
number of parameter: 26269837
| module   | #parameters or shape   | #flops   |
|:---------|:-----------------------|:---------|
| model    | 26.27M                 | 1.515G   |
|  0       |  3.712K                |  3.801M  |
|  1       |  1.476M                |  0.605G  |
|  2.0     |  1.181M                |  0.302G  |
|  3       |  23.599M               |  0.604G  |
|  4       |  10.251K               |  10.24K  |
```
