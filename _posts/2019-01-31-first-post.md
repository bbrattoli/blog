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

Things started to change in 2017 when a Google Residence student succesfully implemented an LSTM which creates the architecture layer by layer, in order to optimize the validation accuracy on CIFAR-10 using roughly 800 gpus for several weeks. At the time this created a lot of hype on the topic, however not many groups had that kind of computational power. In roughly two years the field evolved until it is now possible to outperform the initial success of Google using a single gpu for half a day. This post is intend to summarize the milestone from the first paper until today.

**Disclaimer**: I cannot cover all papers on the topic, thus I will focus on few which I personally found of interest. If you feel that some majour work has been left out, please send me an email, I am always interested in learning new things.

## Past
Until recently Google had the monopoly on the field, by publishing a series of papers (all from the original V.le team) and implementing a commercial product called AutoML which optimizes the network architecture for the specific task of the client. Just to give you a feeling of how quickly NAS went from research to production, recently Waymo announced a [collaboration with GoogleAI](https://medium.com/waymo/automl-automating-the-design-of-machine-learning-models-for-autonomous-driving-141a5583ec2a) for using AutoML to improve the self-driving car system. 

![Waymo tweet on the collaboration with AutoML]({{ site.baseurl }}/assets/img/post_NAS/waymo_tweet.png)

In this section I will give some more insights into three main papers from the Google team.

### Zoph and V.le
As already mentioned in the introuduction, the first NAS model was implemented bye a student during his [Google Residency](https://ai.google/research/join-us/ai-residency/) program (which I personally think it gives an extra spin to the story). Their work was published at ICLR17 with the title [Neural Architecture Search with Reinforcement Learning](https://arxiv.org/abs/1611.01578). 
The model is overall quite simple: a recurrent neural network (two-layer LSTM), called controller, select a specific parameter of the network architecture per each step. In particular, the controller defines: filter hight and width, stride height and width, anchor point (for allowing skip connections) and number of filters. The parameters are chosen layer-by-layer, which means that the first 6 steps of the controller define the first layer, step 7 to 12 define the second layer of the final architecture, and so on untile the desired depth of the network is reached.
The controller learn by training the produced architecture on the training set of CIFAR-10 and evaluating on the validation set. This last evaluation is used as feedback signal for the controller, basically says to the controller if it did a good job or not. Since we cannot differentiate the validation loss with the decision process of the controller, more generally speacking there is no direct connection between the controller decision and the final loss, it is not possible to train the controller end-to-end with SGD. This is where Reinforcment Learning comes into rescue. Without going too much into details (I don't want to make this post a technical report), the validation accuracy is used as a reward function: high reward = controller did good, low reward = controller did bad. The controller can then be updated using REINFORCE by maximizing the expected reward using SGD.
As you can imagine, training the controller for producing the final "optimal" architecture is extremely costly since it is needed to train each single architecture until it converges. The final result reaches comparable performances with hand-crafted architecures, however it does not scale to Imagenet having 1.2M images for training and 1000 classes. The next work will focus exactly on the scalability issue.

### NASNet

### AmoebaNet

## Present

## Future

### GHN

### DARTS

### What now?

## references


