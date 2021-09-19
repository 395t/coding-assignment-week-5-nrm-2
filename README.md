<b><font size=5>CIFAR-10 Task – Object Recognition in Images </font></b>

<font size=3>The CIFAR-10 is a computer vision data consists of 60,000 (32×32) color images in 10 classes, with 6000 images per class.</font>

<b><font size=5>Task and Model </font></b>

<font size=3> The purpose of this dataset and task is to demonstrate the effects of the Batch Normalization on VGG architecture for reducing the loss over the set of epochs and improving the accuracy.  The dataset loading and batch normalization is performed using Keras and tensor flow liberaries.Initially, an extremely simple model was used which yielded accuracies between 70-75. However, as these results were found unsatisfactory, we decided to use a model inspired by vgg16. The model was initially tested for 5 epochs with a batch size of 10. The numbers of epochs were increased to 150 and batch size to 128 to compare the loss and accuracy.</font>


<b><font size=5>Results</font></b>


<img src="Training loss across all models for CIFAR10.png">


```python

```
