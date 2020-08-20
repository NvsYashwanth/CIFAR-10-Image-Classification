# CIFAR-10 Image Classification using PyTorch
[![ForTheBadge built-with-love](http://ForTheBadge.com/images/badges/built-with-love.svg)](https://github.com/NvsYashwanth)

![](https://badgen.net/badge/Code/Python/blue?icon=https://simpleicons.org/icons/python.svg&labelColor=cyan&label)        ![](https://badgen.net/badge/Library/Pytorch/blue?icon=https://simpleicons.org/icons/pytorch.svg&labelColor=cyan&label)       ![](https://badgen.net/badge/Tools/pandas/blue?icon=https://simpleicons.org/icons/pandas.svg&labelColor=cyan&label)       ![](https://badgen.net/badge/Tools/numpy/blue?icon=https://upload.wikimedia.org/wikipedia/commons/1/1a/NumPy_logo.svg&labelColor=cyan&label)        ![](https://badgen.net/badge/Tools/matplotlib/blue?icon=https://upload.wikimedia.org/wikipedia/en/5/56/Matplotlib_logo.svg&labelColor=cyan&label)

The `CIFAR-10` dataset consists of 60000 32x32 colour images in 10 classes, with 6000 images per class. There are 50000 training images and 10000 test images.
The dataset is divided into five training batches and one test batch, each with 10000 images. The test batch contains exactly 1000 randomly-selected images from each class. The training batches contain the remaining images in random order, but some training batches may contain more images from one class than another. Between them, the training batches contain exactly 5000 images from each class.

Here are the classes in the dataset, as well as 10 random images from each:
![](https://github.com/NvsYashwanth/CIFAR-10-Image-Classification/blob/master/Images/cifar10.png)

## Results
***`A validation dataset of size 10,000 was deduced from the Training dataset with its size being changed to 40,000. We train the following models for 50 epochs.`***

### Prarameters Initialization
* Both models have been initialized with random weights sampled from a normal distribution and bias with 0.
* These parameters have been intialized only for the Linear layers present in both of the models.
* If `n` represents number of nodes in a Linear Layer, then weights are given as a sample of normal distribution in the range `(0,y)`. Here `y` represents standard deviation calculated as `y=1.0/sqrt(n)`
* Normal distribution is chosen since the probability of choosing a set of weights closer to zero in the distribution is more than that of the higher values. Unlike in Uniform distribution where probability of choosing any value is equal.

***Model - 1 : FFNN***
* This `Linear Model` uses 3072 nodes at input layer, 2048, 1024, 512, and 256 nodes in the first, second, third and fourth hidden layers respectively, with ouput layer of 10 nodes (10 classes).
* The test accuracy is ***52.81%*** (***This result uses dropout probability of 25%***)
* A  `FNet_model.pth` file has been included. With this one can directly load the model state_dict and use for testing.

***Model - 2 : CNN***
* The `Convolutional Neural Netowork` has 4 convolution layers and pooling layers with 2 fully connected layers. The first convolution layer takes in a channel of dimension 3 since the images are RGB. The kernel size is chosen to be of size 3x3 with stride of 1. The output of this convolution is set to 16 channels which means it will extract 16 feature maps using 16 kernels. We pad the image with a padding size of 1 so that the input and output dimensions are same. The output dimension at this layer will be 16 x 32 x 32. The we apply RelU activation to it followed by a max-pooling layer with kernel size of 2 and stride 2. This down-samples the feature maps to dimension of 16 x 16 x 16.
* The second convolution layer will have an input channel size of 16. We choose an output channel size to be 32 which means it will extract 32 feature maps. The kernel size for this layer is 3 with stride 1. We again use a padding size of 1 so that the input and output dimension remain the same. The output dimension at this layer will be 32 x 16 x 16. We then follow up it with a RelU activation and a max-pooling layer with kernel of size 2 and stride 2. This down-samples the feature maps to dimension of 32 x 8 x 8.
* The third convolution layer will have an input channel size of 32. We choose an output channel size to be 64 which means it will extract 64 feature maps. The kernel size for this layer is 3 with stride 1. We again use a padding size of 1 so that the input and output dimension remain the same. The output dimension at this layer will be 64 x 8 x 8. We then follow up it with a RelU activation and a max-pooling layer with kernel of size 2 and stride 2. This down-samples the feature maps to dimension of 64 x 4 x 4.
* The fourth convolution layer will have an input channel size of 64. We choose an output channel size to be 128 which means it will extract 128 feature maps. The kernel size for this layer is 3 with stride 1. We again use a padding size of 1 so that the input and output dimension remain the same. The output dimension at this layer will be 128 x 4 x 4 followed up it with a RelU activation and a max-pooling layer with kernel of size 2 and stride 2. This down-samples the feature maps to dimension of 128 x 2 x 2.
* Finally, 3 fully connected layers are used. We will pass a flattened version of the feature maps to the first fully connected layer. The fully connected layers have 512 nodes at input layer, 256, 64 nodes in the first and second hidden layers respectively, with ouput layer of 10 nodes (10 classes). So we have two fully connected layers of size 512 x 256 followed up by 256 x 64 and 64 x 10.
* The test accuracy is ***78.23%*** (***This result uses dropout probability of 25%***)
* A `convNet_model.pth` file has been included. With this one can directly load the model state_dict and use for testing.

<p align='center'>
  <img src='https://github.com/NvsYashwanth/CIFAR-10-Image-Classification/blob/master/Images/cifar%20loss%20curve.png'>
</p>
