# LeNet Recognizing Traffic Signs

The original [LeNet-5] with adapted fully connected layers to classify [traffic signs].

![lenet5_arch](https://user-images.githubusercontent.com/33037020/193161551-7e55966e-d241-4771-9741-c9aff18bfff0.PNG)

---

## Problem Overview

Traffic sign recognition is a very important and practical task, especially in the context of autonomous cars. There are many datasets for this task, simpler ones with only 4 different classes and more complex ones with more than a thousand classes. In here we investigate one of the most popular ones, the [German Traffic Sign Recognition Benchmark (GTSRB)].

Consisting of 43 different classes, each one constituted by a unique german traffic sign plate, the GTSRB dataset has more than 50.000 real-world images of varying resolutions. It is considered a hard dataset since some of its images are bad in quality, having poor lighting and being so blurred or jittered that even humans may not be able to identify the sign. The image grid below sheds light on the images we are working with:

![traffic_signs](https://user-images.githubusercontent.com/33037020/192881857-f79be892-4883-4adc-bd69-a51e8277e91f.PNG)

Convolutional Neural Networks (CNNs) are known for being able to deal with image classification in hard scenarios. They have the ability of capturing features in data (and interactions between these features) that are very subtle, invisible to human eyes. Therefore, our problem may become more easily tractable with a well-established CNN, like the LeNet.

## Analysis Introduction

[LeNet] is a very popular, and also very old, CNN. In fact, it is one of the neural networks that introduced and popularized convolutional neural networks in the field of machine learning. It was originally proposed to classify handwritten digits in images and, since then, many adaptations to it have been proposed.

The objective here is to show how one of the original LeNet architectures, LeNet-5, can be easily adapted to work in different settings of image classification. We take all convolutional, average pooling and fully connected layers of the original work and just swap the top layer, a fully connected with 10 neurons, with another fully connected with 43 neurons. 43 is the number of classes in our problem. We build and train this new architecture from scratch in our traffic signs dataset using [TensorFlow].

In the end, we are able to achieve 87% accuracy on our, mostly raw, traffic signs dataset. Mostly raw because all we do is rescale the images to 32x32, as needed by the LeNet-5, and change their color scheme to grayscale. This means that we do not add anything to the images, just use the information already available in them. The performance of LeNet-5 is respectable, considering that it was first proposed in the 1990s to work in a simpler problem. The confusion matrix below illustrates the performance of the model; the main diagonal indicates correct predictions:

![confusion_matrix_traffic_signs_large](https://user-images.githubusercontent.com/33037020/192904844-a57b7a6d-25e3-499d-9783-d1c6775ba25a.PNG)

As most real-world small images, ours have an overall bad quality. Other than that, classes are heavily unbalanced. Some classes have more than 10 times the amount of instances of others. Even if not being in our scope, we argue that image preprocessing and data augmentation for class balancing would probably help in this task. Conclusively, we show an image grid summarizing the predictions of our reworked LeNet-5:

![traffic_signs_predicted](https://user-images.githubusercontent.com/33037020/192904868-2b4b37e6-96ec-43e8-b564-3516a9c0303c.PNG)

[//]: #

[traffic signs]: <https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign>
[German Traffic Sign Recognition Benchmark (GTSRB)]: <https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign>
[LeNet-5]: <http://yann.lecun.com/exdb/publis/pdf/lecun-01a.pdf>
[LeNet]: <http://yann.lecun.com/exdb/publis/pdf/lecun-01a.pdf>
[TensorFlow]: <https://www.tensorflow.org>
