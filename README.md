# ComputerVisionGAN
Image-to-Image Translation with CycleGAN in PyTorch for Intro to Computer Vision UChicago

**Project Overview:** Utilizing two sets of images, train two generators that can convert an image from one dataset to the other. In this case, we utilized one set of images of older individuals, in this case over 70, and one set of images of younger individuals, in this case between 20 and 40. With these two datasets, we aimed to train generators that essentially were capable of aging and de-aging faces.
The goal in choosing these two sets of images was to have similarly defined images with facial features in comparably similar places, such that the models were able to recognize features and better generate fake images.

**Parameters:** The main parameters of choice were learning rate, which was set to 0.00002, and batch size, which was set to 32.

**Generator Model:** We used the same model for the generator in each direction, consisting mainly of 2d convolutional layers, with an adjustable number of middle blocks.

**Discriminator Model:** We used the same model for the discriminator in each direction, consisting of three identical blocks of 3 layers, 2d convolution, 2d instance normalization, and Leaky ReLU activation, after an initial block of just 2d convolution and Leaky ReLU activation, because less stabilization is needed amongst the first layers.

**Dataset Description:** We took a dataset of faces and split it in two, filtering images of people between the age of 20 and 40 into a “young” dataloader, images of people above 70 into an “old” dataloader, and discarding the rest. There were 1446 “old” faces and 3717 “young” faces.These images were all head-on portrait photos of individuals with a variety of facial features and expressions, all cropped to about the head of the individual, and with a variety of different image qualities.

**Obstacles:** Throughout the training and creation of this model, we encountered several obstacles, from finding proper datasets to generate between -- our first attempt had too much variation in both sides of the dataset -- to getting a training model to run long enough to produce meaningful results. Most notably in terms of model performance, we encountered spots and blotches in images as the learning rate increased, leading us to prefer a small learning rate to reduce blotches entirely. Beyond minor missteps because of glitches, the rest of the results were relatively simple.

**Sources:** https://www.kaggle.com/datasets/frabbisw/facial-age, https://www.kaggle.com/code/songseungwon/cyclegan-tutorial-from-scratch-monet-to-photo, https://debuggercafe.com/pytorch-imagefolder-for-training-cnn-models/, https://medium.com/@chilldenaya/cyclegan-introduction-pytorch-implementation-5b53913741ca, https://machinelearningmastery.com/cyclegan-tutorial-with-keras/

Final results:

![Old to Young Faces](Old%20to%20Young.png)
![Young to Old Faces](Young%20to%20Old.png)
