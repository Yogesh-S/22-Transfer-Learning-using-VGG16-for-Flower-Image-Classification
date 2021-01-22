# 22-Transfer-Learning-using-VGG16-for-Flower-Image-Classification

Most of the time we don't want to train a whole convolutional network ourselves. Modern ConvNets training on huge datasets like ImageNet take weeks on multiple GPUs.
Instead, most people use a pretrained network either as a fixed feature extractor, or as an initial network to fine tune.

Transfer learning involves taking a pre-trained neural network and adapting the neural network to a new, different data set.

Depending on both:

> The size of the new data set, and

> The similarity of the new data set to the original data set

The approach for using transfer learning will be different. There are four main cases:

![alt text](https://github.com/Yogesh-S/22-Transfer-Learning-using-VGG16-for-Flower-Image-Classification/blob/main/TransferLearning.JPG?raw=true)

---
In this notebook, we'll be using [VGGNet](https://arxiv.org/pdf/1409.1556.pdf) trained on the [ImageNet dataset](http://www.image-net.org/) as a feature extractor. Below is a diagram of the VGGNet architecture, with a series of convolutional and maxpooling layers, then three fully-connected layers at the end that classify the 1000 classes found in the ImageNet database.

![alt text](https://github.com/Yogesh-S/22-Transfer-Learning-using-VGG16-for-Flower-Image-Classification/blob/main/vgg_16_architecture.png?raw=true)

VGGNet is great because it's simple and has great performance, coming in second in the ImageNet competition. The idea here is that we keep all the convolutional layers, but **replace the final fully-connected layer** with our own classifier. This way we can use VGGNet as a _fixed feature extractor_ for our images then easily train a simple classifier on top of that. 
* Use all but the last fully-connected layer as a fixed feature extractor.
* Define a new, final classification layer and apply it to a task of our choice!

More about transfer learning is available at [the CS231n Stanford course notes](http://cs231n.github.io/transfer-learning/).
