## Flower GAN
![Python 3.6](https://img.shields.io/badge/python-3.6-brightgreen)
![TensorFlow Versions](https://img.shields.io/badge/TensorFlow-2.0+-blue.svg)

A **Generative Adversarial Network (GAN)** consists of two contesting Neural Networks in the form of a zero-sum game, where one agent's gain is another agent's loss.
- Generator 
- Discriminator

The core idea that rules GANs is based on the “indirect” training through the Discriminator that is also getting updated dynamically. This basically means that the generator is not trained to minimize the distance to a specific image, but rather to fool the discriminator. This enables the model to learn in an unsupervised manner.

In my first personal attempt at a GAN, I've chosen to do flowers, 
I'd say flowers added an element of difficulty to it, unlike human faces or cars, apart from the hole in the centre of many flowers, the rest of the flower is usually non-standard, and the GAN did along the way produce some funky imagery.


To do this, we will feed the Discriminator the following sample images:

![Flower1](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Sample%20pictures/image_07963.jpg)
![Flower2](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Sample%20pictures/image_08112.jpg)

As you may have noticed, these are *high* resolution images, and a *deeper convolutional network* is required to extract intricate features from these images, even after resizing the pictures. However, I do have computational resource limits, so I've tried several architectures, and found one that works eventually. 

The results are pretty cool, 
![Output1](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Output%20pictures/Flower_GAN_plot_v5_10300.png)
![Output2](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Output%20pictures/Flower_GAN_plot_v5_9200.png)
