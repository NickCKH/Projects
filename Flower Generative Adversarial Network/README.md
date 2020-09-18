## Flower GAN
![Python 3.6](https://img.shields.io/badge/python-3.6-brightgreen)
![TensorFlow Versions](https://img.shields.io/badge/TensorFlow-2.0+-blue.svg)

A **Generative Adversarial Network (GAN)** consists of two contesting Neural Networks in the form of a zero-sum game, where one agent's gain is another agent's loss.
- Generator 
- Discriminator

Not gonna explain everything but here's a decent explanation:
https://en.wikipedia.org/wiki/Generative_adversarial_network

The core idea that rules GANs is based on the “indirect” training through the Discriminator that is also getting updated dynamically. This basically means that the generator is not trained to minimize the distance to a specific image, but rather to fool the discriminator. This enables the model to learn in an unsupervised manner.

In my first personal attempt at a GAN, I've chosen to do flowers, 
I'd say flowers added an element of difficulty to it, unlike human faces or cars, apart from the hole in the centre of many flowers, the rest of the flower is usually non-standard, and the GAN did along the way produce some funky imagery.


To do this, we will feed the Discriminator the following sample images:

![Flower1](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Sample%20pictures/image_07963.jpg)
![Flower2](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Sample%20pictures/image_08112.jpg)

As you may have noticed, these are *high* resolution images, and a *deeper convolutional network* is required to extract intricate features from these images, even after resizing the pictures. However, I do have computational resource limits, so I've tried several architectures, and found one that works eventually. The results are pretty cool, basically we feed the Generator Neural Network some Gaussian noise in the shape of the output images we want:

![Input1](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Input%20pictures/Flower_GAN_plot_v5_500.png)


After a back and forth of succeeding and failing to trick the Discriminator thousands of times, the Generator eventually gets good at generating flowers, and outputs stuff like these: 

![Output1](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Output%20pictures/Flower_GAN_plot_v5_10300.png)
![Output2](https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Output%20pictures/Flower_GAN_plot_v5_9200.png)

Cool stuff, you can check out the full code in the notebook below: 
https://github.com/NickCKH/Projects/blob/master/Flower%20Generative%20Adversarial%20Network/Flowers_Adversarial_Network_v3.ipynb





