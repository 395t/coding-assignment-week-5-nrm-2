# Normalization Methods - Week 5 Group 2

Our group covered the following normalization methods and papers,
* **Group Normalization** - [Group Normalization](https://arxiv.org/abs/1803.08494), Wu, He, 2018
* **No Normalization with Gradient Clipping** - [High-Performance Large-Scale Image Recognition Without Normalization](https://arxiv.org/abs/2102.06171), Brock, De, Smith, Simonyan; 2021
* **Batch-Channel Normalization** - [Micro-Batch Training with Batch-Channel Normalization and Weight Standardization](https://arxiv.org/abs/1903.10520), Qiao, Wang, Liu, Shen, Yuille; 2019
* **Batch Normalization** - [Understanding Batch Normalization](https://arxiv.org/abs/1806.02375), Bjorck, Gomes, Selman, Weinberger; 2018
* **Batch Normalization** - [Rethinking "Batch" in BatchNorm](https://arxiv.org/abs/2105.07576), Wu, Johnson; 2021


We used the following image classification datasets to test the effectiveness of these normalizations methods.
## Datasets
* CIFAR10
* STL10
* Caltech100


We tested the following normalization methods on the [VGG11](https://arxiv.org/abs/1409.1556) model architecture.

## Normalization Types
* **Group Normalization**: `torch.nn.GroupNorm(in,out)`
* **Gradient Clipping**: `torch.nn.utils.clip_grad_norm_()`
* **Batch Channel Weight Normalization** [BCN Author's GitHub](https://github.com/joe-siyuan-qiao/Batch-Channel-Normalization) [WS Author's GitHub](https://github.com/joe-siyuan-qiao/WeightStandardization)
* **Batch Normalization** `torch.nn.BatchNorm2d()`

=======
## CIFAR-10 Task – Object Recognition in Images

### Description

<font size=3>The CIFAR-10 is a computer vision data consists of 60,000 (32×32) color images in 10 classes, with 6000 images per class.</font>

<b><font size=5>Task and Model </font></b>

<font size=3> The purpose of this dataset and task is to demonstrate the effects of the different normalization methods on VGG architecture for reducing the loss over the set of epochs and improving the accuracy.  The dataset loading and batch normalization is performed using Pytorch and Torchvision libraries.  The model was initially tested for 5 epochs with a batch size of 10. The numbers of epochs were increased to 150 and batch size to 128 to compare the loss and accuracy.</font>

### Results

Results were obtained on a VGG11 model architecture with `learning rate = 1e-4` and Adam optimizer.

#### Loss

When we first look at training loss, we can see all normalization methods converging at about the same rate, with Group Normalization converging at higher loss than the others.  A similar convergence can be seen with the validation loss.

<img src="figure/Training loss across all models for CIFAR10.png">

<img src="figure/Validation loss across all models for CIFAR10.png">

#### Accuracy

In terms of accuracy, batch normalization surpasses all other normalizations on the CIFAR-10 dataset.  Gradient Clipping actually competes closely with Batch Normalization given enough epochs, and again Group Normalization lags behind the other methods' accuracy for both training and validation.

<img src="figure/Validation accuracy across all models for CIFAR10.png">

<img src="figure/Training accuracy across all models for CIFAR10.png">


## STL10

### Description

The STL10 dataset consists of 96x96 labeled images used for Image Classification. It provides a similar challenge as CIFAR-10, but with a smaller training set. The training set contained 5000 images while there are 8000 images in the test set. We also ignored the unlabeled training set provided for unsupervised training purposes. This dataset was a good test to see how well the different normalization techniques can generalize with a smaller training sample size. 

### method

Like the previous dataset, we trained VGG11 for 10 epochs with adam optimizer with initial *lr = 1e-4*, and a batch size of 128 image.

### Result

#### Loss

First we can note that Batch Channel Weight Normalization achieved the lowest training loss but converged to about the same validation loss as the other normalization methods.  Not much else can be said about our loss results other than most methods converged to similar values for validation loss with Batch Channel Weight Normalization and Batch Normalization converging earlier than Gradient Clipping and Group Normalization.

<img src="figure/Training loss across all models for STL10.png">

<img src="figure/Validation loss across all models for STL10.png">

#### Accuracy

We see a similar story to the loss curves when we look at the accuracy results.  Both Batch Channel Weight Normalization and Batch Normalization converge at their highest validation accuracy earlier, but the other two methods achieve similar results given enough iterations.

<img src="figure/Validation accuracy across all models for STL10.png">

<img src="figure/Training accuracy across all models for STL10.png">

#### Batch Size analysis with STL10

Using vgg16 with the Adam optimizer over 10 epochs, a smaller (32) and larger (512) batch size were tested with batch channel normalization with weight standardization and batch normalization. 

<img src="figure/stl10 different batch sizes (training loss).png">

<img src="figure/stl10 different batch sizes (test loss).png">

As seen from the results above, the smaller batch size was able to generalize the training set better and provide lower loss in the test results. The low training loss of BCN+WS with a batch size of 512 suggests that it was overfitting the data. This is especially critical with STL10 since the training set is so small. 

## Caltech256

### Description

Caltech 256 is a much richer dataset that splits around 30k real world image to 257 groups. Each class is guranteed to have at least 80 image.

### method

Like previous dataset, we trained VGG11 for 10 epoch with adam optimizer with initial *lr = 1e-4*, and a batch size of 128 image. For every 10 batch, a valdation set of roughly 500 image is randomly picked and evaluated. 

### Result

We reported on the training/evaluation loss and their accuracy below.

#### Loss

Due to the more rich dataset, we see a stronger difference between the loss graphs of our normalizations compared to the previous datasets.  Batch Channel Weight Normalization actually converges at a lower training loss than Batch Normalization, but Batch Normalization achieves a lower validation loss than all other methods.  The fact that Batch Channel Weight Normalization does the worst with validation loss implies that its low training loss may be due to overfitting.

<img src="figure/Training loss across all models for CALTECH256.png">

<img src="figure/Validation loss across all models for CALTECH256.png">

#### Accuracy

In terms of validation accuracy, Batch Normalization again surpasses the other methods, this time by a sizable margin.  Gradient Clipping maintains the most competitive distance but always falls short of batch norm accuracy across all iterations.

<img src="figure/Validation accuracy across all models for CALTECH256.png">

<img src="figure/Training accuracy across all models for CALTECH256.png">

### TL;DR
* As expected, batch norm performs the best across all datasets. 
* Gradient Clipping (No Normalization) is still comparable to Batch Normalization
* Group Normalization consistently performs the worst.
