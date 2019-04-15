# Real-Time Facial Emotion Recognition

<img alt="GitHub followers" src="https://img.shields.io/github/followers/maelfabien.svg?style=social"> <img alt="GitHub contributors" src="https://img.shields.io/github/contributors-anon/maelfabien/Multimodal-Emotion-Recognition.svg"> <img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/y/maelfabien/Multimodal-Emotion-Recognition.svg"> <img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/3.svg">

Table of Content :
- [I. Context](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#i-context)
- [II. Data Sources](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#ii-data-sources)
- [III. Downloads](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#iii-download)
- [IV. Methodology](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#iv-methodology)
- [V. How to use it ?](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#v-how-to-use-it-)
- [VI. Demonstration](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#vi-demonstration)
- [VII. Deployment](https://github.com/maelfabien/Multimodal-Emotion-Recognition/blob/master/README.md#viii-deployment) 

In this project, I am exploring state of the art models in facial emotion recognition. 

## I. Context

Affective computing is a field of Machine Learning and Computer Science that studies the recognition and the processing of human affects. 

Facial Emotion Recognition is a classic discipline that aims to interpret video inputs and analyze emotions from the face. Facial emotion recognition is widely used, especially for :
- interview practice
- customer satisfaction
- discussion automatic classification
- ...

## II. Data Sources

I am using the popular FER2013 Kaggle Challenge data set. The data consists of 48x48 pixel grayscale images of faces. The faceshave been automatically registered so that the face is more or less centered andoccupies about the same amount of space in each image. The data set remainsquite challenging to use, since there are empty pictures, or wrongly classified images. https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data

## III. Download

| Data | Processed Data (for training) | Pre-trained Model | Colab Notebook |Other |
| --- | --- | --- | --- | --- |
| [here](https://drive.google.com/file/d/1hWqVdOYNvCuioiDk-CBgMtKOgl05aA--/view?usp=sharing) | [X-train](https://drive.google.com/file/d/14xs-0nZNQuuMdtTOwqcJQm_GZ_rTO8mB/view?usp=sharing) [y-train](https://drive.google.com/file/d/1EX5KkPquwpHD9ZKpTxGhk3_RFmVDD8bf/view?usp=sharing) [X-test](https://drive.google.com/file/d/1TFH3kvGDS0iWjqKYo3lZuIu65I9h0LYr/view?usp=sharing) [y-test](https://drive.google.com/file/d/1HTzGc_J4kTQRFvLIvcMQA3mt6PnyNT53/view?usp=sharing) |  [Weights](https://drive.google.com/file/d/1-L3LnxVXv4vByg_hqxXMZPvjKSQ12Ycs/view?usp=sharing) [Model](https://drive.google.com/file/d/1_dpHN9L6hsQYzTX2zk9K5JF2CZ1FOcZh/view?usp=sharing) | [Colab Notebook](https://colab.research.google.com/drive/1dV1IvYLV24vXGvyzMFNAA18csu8btV2-) | [Face Detect Model](https://drive.google.com/file/d/18YMrAStwXbN-aPZ45ylNrdAXQQPJx0Hd/view?usp=sharing) |

## IV. Methodology

My aim is to develop a model able to provide a live emotion recognition with a visual user interface. I am therefore trying to display information in a clear way, and handle multi-face data.

### Video Processing

#### Pipeline

The video processing pipeline was built the following way :
- Launch the webcam
- Identify the face by Histogram of Oriented Gradients
- Zoom on the face
- Dimension the face to 48 * 48 pixels
- Make a prediction on the face using our pretrained model
- Also identify the number of blinks on the facial landmarks on each picture

#### Model

The model I have chosen is an XCeption model, since it outperformed the other approaches we developped so far. I tuned the model with :
- data augmentation
- early stopping
- decreasing learning rate on plateau
- L2-Regularization
- Class weight balancing
- And kept the best model

As you might have understood, the aim was to limit overfitting as much as possible in order to obtain a robust model. 

- To know more on how I prevented overfitting, check my article : https://maelfabien.github.io/deeplearning/regu/
- To know more on the XCeption model, check my article : https://maelfabien.github.io/deeplearning/xception/

![image](/Images/model_fit.png)

The XCeption architecture is based on DepthWise Separable convolutions that allow to train much fewer parameters, and therefore reduce training time on Colab's GPUs to less than 90 minutes.

![image](/Images/video_pipeline2.png)

## V. How to use it ?

I will soon by publishing `.py` files with all the required content to launch easily the algorithm on your own computer. Meanwhile, you can run the notebooks I am providing and try the algorithm yourself. I will also be providing an app in the future using Render.

## VI. Demonstration

![image](/Images/Face.gif)

## VII. Deployment

The app will soon be available based on this template : https://github.com/render-examples/fastai-v3
