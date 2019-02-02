---
layout: post
title: Neural Architecture Search
subtitle: past, present and future
tags: [NAS, MetaLearning]
feature-img: assets/img/sample_feature_img.png
hide: false
---
Summary into the past, present and future of Neural Architecture Search (NAS). 

## What is NAS?
Neural Architecture search (as the name suggests) are machine learning algorithms for automatic search of neural network architecture. 
Anyone who had contact with deep learning knows that finding the hyperparameters is very costly and takes most of the computational effort. The cost becames huge when you want to optimize the network architecture to the specific task, in particular defining the number of layers, the activation per layer, the number of filters per convolution, the skip connections, etc... Typically researchers (like me) do not care about the optimizing the architecture, since we are constraint by using the same architecture we are comparing our method with. However, optimizing the architecture for a specific task is crucial for industry, where deep learning engineers spend most of their time on the problem.

Things started to change in 2017 when a Google Residence student succesfully implemented an LSTM which creates the architecture layer by layer, in order to optimize the validation accuracy on CIFAR-10 using roughly 800 gpus for several weeks. At the time this created a lot of hype on the topic, however not many groups had that kind of computational power. In a little more than one year the field evolved until it is now possible to outperform the initial success of Google using a single gpu for half a day. This post is intend to summarize the milestone from the first paper until today.

**Disclaimer**: I cannot cover all papers on the topic, thus I will focus on few which I personally found of interest. If you feel that some majour work has been left out, please send me an email, I am always interested in learning new things.

## Past
Until recently Google had the monopoly on the field, by publishing a series of papers (all from the original V.le team) and implementing a commercial product called AutoML which optimizes the network architecture for the specific task of the client. Just to give you a feeling of how quickly NAS went from research to production, recently Waymo announced a [collaboration with GoogleAI](https://medium.com/waymo/automl-automating-the-design-of-machine-learning-models-for-autonomous-driving-141a5583ec2a) for using AutoML to improve the self-driving car system. 

![Waymo tweet on the collaboration with AutoML](/assets/img/post_NAS/waymo_tweet.png)

In this section I will give some more insights into three main papers from the Google team.

### Zoph and V.le

### NASNet

### AmoebaNet

## Present

## Future

### GHN

### DARTS

### What now?

## references


