<<<<<<< HEAD
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
* **Batch Channel Weight Normalization** 

=======
## CIFAR-10 Task – Object Recognition in Images

### Description

<font size=3>The CIFAR-10 is a computer vision data consists of 60,000 (32×32) color images in 10 classes, with 6000 images per class.</font>

<b><font size=5>Task and Model </font></b>

<font size=3> The purpose of this dataset and task is to demonstrate the effects of the Batch Normalization on VGG architecture for reducing the loss over the set of epochs and improving the accuracy.  The dataset loading and batch normalization is performed using Keras and tensor flow liberaries.Initially, an extremely simple model was used which yielded accuracies between 70-75. However, as these results were found unsatisfactory, we decided to use a model inspired by vgg16. The model was initially tested for 5 epochs with a batch size of 10. The numbers of epochs were increased to 150 and batch size to 128 to compare the loss and accuracy.</font>

### Method

### Results

#### Loss

<img src="figure/Training loss across all models for CIFAR10.png">

<img src="figure/Validation loss across all models for CIFAR10.png">

#### Accuracy

<img src="figure/Validation accuracy across all models for CIFAR10.png">

<img src="figure/Training accuracy across all models for CIFAR10.png">


## STL10

### Description

### method

### Result

#### Loss

<img src="figure/Training loss across all models for STL10.png">

<img src="figure/Validation loss across all models for STL10.png">

#### Accuracy

<img src="figure/Validation accuracy across all models for STL10.png">

<img src="figure/Training accuracy across all models for STL10.png">

## Caltech256

### Description

Caltech 256 is a much richer dataset that splits around 30k real world image to 257 groups. Each class is guranteed to have at least 80 image.

### method

Like previous dataset, we trained VGG11 for 10 epoch with adam optimizer with initial *lr = 1e-4*, and a batch size of 128 image. For every 10 batch, a valdation set of roughly 500 image is randomly picked and evaluted. 

### Result

We reported on the training/evaluation loss and their accuracy below:

#### Loss

<img src="figure/Training loss across all models for CALTECH256.png">

<img src="figure/Validation loss across all models for CALTECH256.png">

#### Accuracy

<img src="figure/Validation accuracy across all models for CALTECH256.png">

<img src="figure/Training accuracy across all models for CALTECH256.png">

As expected, batch norm performs the best across all cases. 
>>>>>>> 19c49046f861835dbbdd47e7a942942f6a633016
