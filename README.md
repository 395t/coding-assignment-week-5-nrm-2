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



































## Reference

Any code that you borrow or other reference should be properly cited.


CIFAR-10 Task – Object Recognition in Images
The CIFAR-10 is a computer vision data consists of 60,000 (32×32) color images in 10 classes, with 6000 images per class.
Task and Model
The purpose of this dataset and task is to demonstrate the effects of the Batch Normalization on VGG architecture for reducing the loss over the set of epochs and improving the accuracy.  The dataset loading and batch normalization is performed using Keras and tensor flow liberaries.Initially, an extremely simple model was used which yielded accuracies between 70-75. However, as these results were found unsatisfactory, we decided to use a model inspired by vgg16 [2]. The model was initially tested for 5 epochs with a batch size of 10. The numbers of epochs were increased to 150 and batch size to 128 to compare the loss and accuracy.
Results
Starting epoch 1
Loss after mini-batch   500: 2.127
Loss after mini-batch  1000: 2.017
Loss after mini-batch  1500: 1.949
Loss after mini-batch  2000: 1.908
Loss after mini-batch  2500: 1.882
Loss after mini-batch  3000: 1.866
Loss after mini-batch  3500: 1.847
Loss after mini-batch  4000: 1.818
Loss after mini-batch  4500: 1.806
Loss after mini-batch  5000: 1.787
Starting epoch 2
Loss after mini-batch   500: 1.762
Loss after mini-batch  1000: 1.737
Loss after mini-batch  1500: 1.737
Loss after mini-batch  2000: 1.712
Loss after mini-batch  2500: 1.718
Loss after mini-batch  3000: 1.724
Loss after mini-batch  3500: 1.703
Loss after mini-batch  4000: 1.685
Loss after mini-batch  4500: 1.699
Loss after mini-batch  5000: 1.688

Decrease in loss gradually when batch normalization is applied.



Starting epoch 1
Loss after mini-batch   500: 2.146
Loss after mini-batch  1000: 2.050
Loss after mini-batch  1500: 1.979
Loss after mini-batch  2000: 1.934
Loss after mini-batch  2500: 1.906
Loss after mini-batch  3000: 1.905
Loss after mini-batch  3500: 1.883
Loss after mini-batch  4000: 1.852
Loss after mini-batch  4500: 1.845
Loss after mini-batch  5000: 1.830
Starting epoch 2
Loss after mini-batch   500: 1.809
Loss after mini-batch  1000: 1.787
Loss after mini-batch  1500: 1.789
Loss after mini-batch  2000: 1.776
Loss after mini-batch  2500: 1.767
Loss after mini-batch  3000: 1.774
Loss after mini-batch  3500: 1.756
Loss after mini-batch  4000: 1.743
Loss after mini-batch  4500: 1.757
Loss after mini-batch  5000: 1.742

Decrease in loss without batch normalization.
