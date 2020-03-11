# Overview

## GAN

Two neural networks, gonna plat a game.



There is one called the GEENRATOR, and the Discrimninator.



The generator has a random vector, lik a gaussian distriution, and you feed those numbers. And then the genrators will turn that into an image. Called the Fake Sample. Because it was generated.The fake sample is connected to the discriminator.

The discirimnator has one job to do, to look at he images that re comingi n, fake sample and real samples. The only job is to find the real or the fake sample.



generative adversiarial nets 2014 64 64

xander links slide mabe put into gitbook



Stle-Gan

zalando machine learning gan

generative 4x super resolution SRGAN bicup original

suprass the shannon / channel  limit.

neural inpainting photoshop

GLOW gan



50000 images tops out, 10000 is good.



OK to film, and the ncapture the frames.

julian oliver solar driven unit, windmill that powers a computer that mines minero cryptocurrency to find climate change.



### StyleGAN

A **generative adversarial network** \(**GAN**\) is a class of [machine learning](https://en.wikipedia.org/wiki/Machine_learning) systems invented by [Ian Goodfellow](https://en.wikipedia.org/wiki/Ian_Goodfellow) and his colleagues in 2014.[\[1\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-GANnips-1) Two [neural networks](https://en.wikipedia.org/wiki/Neural_network) contest with each other in a game \(in the sense of [game theory](https://en.wikipedia.org/wiki/Game_theory), often but not always in the form of a [zero-sum game](https://en.wikipedia.org/wiki/Zero-sum_game)\). Given a training set, this technique learns to generate new data with the same statistics as the training set. For example, a GAN trained on photographs can generate new photographs that look at least superficially authentic to human observers, having many realistic characteristics. Though originally proposed as a form of [generative model](https://en.wikipedia.org/wiki/Generative_model) for [unsupervised learning](https://en.wikipedia.org/wiki/Unsupervised_learning), GANs have also proven useful for [semi-supervised learning](https://en.wikipedia.org/wiki/Semi-supervised_learning),[\[2\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-ITT_GANs-2) fully [supervised learning](https://en.wikipedia.org/wiki/Supervised_learning),[\[3\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-3) and [reinforcement learning](https://en.wikipedia.org/wiki/Reinforcement_learning).[\[4\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-4) In a 2016 seminar, [Yann LeCun](https://en.wikipedia.org/wiki/Yann_LeCun) described GANs as "the coolest idea in machine learning in the last twenty years".[\[5\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-5)

Generative models are important in science and engineering. They are used for a lot of content generation.

> What I cannot create, I do not understand — Richard Feynman

An agent = A robot.

ML5A github

## Neural Network

Neural networks are a set of algorithms, modeled loosely after the human brain, that are designed to recognize patterns. They interpret sensory data through a kind of machine perception, labeling or clustering raw input. The patterns they recognize are numerical, contained in vectors, into which all real-world data, be it images, sound, text or time series, must be translated.

## KNN

> In pattern recognition, the k-nearest neighbors algorithm \(k-NN\) is a non-parametric method used for classification and regression.\[1\] In both cases, the input consists of the k closest training examples in the feature space. _-_ [Wikipedia](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)



_This information is imported from_ [_https://towardsdatascience.com/r-cnn-fast-r-cnn-faster-r-cnn-yolo-object-detection-algorithms-36d53571365e_](https://towardsdatascience.com/r-cnn-fast-r-cnn-faster-r-cnn-yolo-object-detection-algorithms-36d53571365e)_._

Computer vision is an interdisciplinary field that has been gaining huge amounts of traction in the recent years and self-driving cars have taken centre stage. Another integral part of computer vision is object detection. Object detection aids in pose estimation, vehicle detection, surveillance etc. The difference between object detection algorithms and classification algorithms is that in detection algorithms, we try to draw a bounding box around the object of interest to locate it within the image. Also, you might not necessarily draw just one bounding box in an object detection case, there could be many bounding boxes representing different objects of interest within the image and you would not know how many beforehand.

## R-CNN <a id="bbfe"></a>

To bypass the problem of selecting a huge number of regions, [Ross Girshick et al](https://arxiv.org/pdf/1311.2524.pdf). proposed a method where we use selective search to extract just 2000 regions from the image and he called them region proposals. Therefore, now, instead of trying to classify a huge number of regions, you can just work with 2000 regions. These 2000 region proposals are generated using the selective search algorithm which is written below.

### Problems with R-CNN

* It still takes a huge amount of time to train the network as you would have to classify 2000 region proposals per image.
* It cannot be implemented real time as it takes around 47 seconds for each test image.
* The selective search algorithm is a fixed algorithm. Therefore, no learning is happening at that stage. This could lead to the generation of bad candidate region proposals.

{% embed url="https://medium.com/@jonathan\_hui/object-detection-speed-and-accuracy-comparison-faster-r-cnn-r-fcn-ssd-and-yolo-5425656ae359" %}

## FeatureExtractor

You can use neural networks to recognise the content of images. Most of the time you will be using a "pre-trained" model trained on a large dataset to classify an image into a fixed set of categories. However you can also use a part of the pre-trained model: the [features](https://en.wikipedia.org/wiki/Feature_extraction). Those features allow you to 'retrain' or 'reuse' the model for a new custom task. This is known as [Transfer Learning](https://en.wikipedia.org/wiki/Transfer_learning).

