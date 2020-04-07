---
toc: true
layout: post
description: post about aws
categories: [markdown]
title: AWS Innovate - ML Online Conference
---

# AWS Innovate: ML Online Conference

Last week I attended the AWS Innovate: ML online Conference. 

**Website:** https://aws.amazon.com/events/aws-innovate/machine-learning/

While I work in AWS ecosystem, I don't have much exposure to the ML products/services and tools that AWS provides. This conference was a good way to get broad exposure to the various options and solutions AWS provides. I will admit that as I was watching various sessions I was working and chatting with collogues that were also watching various sessions. 

## Sessions I attended

1. Automate machine Learning: From Debugging DL to detecting model drift in Prod. 
2. Simplify and accelerate time-series forecasting and real-time personalization
3. Amazon Kendra: Reinvent enterprise search and interact with data using AI
4. Large scale image and video analysis with Amazon Rekognition 

## My Take-aways
1. This session was fairly basic and addressed DL debugging tools that AWS SageMaker has to diagnose various issues with your model. The case-study was focused on vanishing gradient problem. For those unfamiliar, the vanishing gradient problem is when the gradients get very small. When the gradient is used to update the weight value there is almost no update so no learning can occur. (think of multiplying two small numbers, 0.1 * 0.1=0.01) The tooling that AWS provides for debugging DL models is really cool - I would definitely use it if I worked in SageMaker. 
Another part of this session was addressing drift. However, the example they used was to monitor the covariate shift /distribution of live data and verify that it has a similar distribution to the training data. I think of that more as a monitoring/validation check than drift. 
2. I caught the last third of the time-series session. This was very validating because AWS' product approaches time-series forecasting the same way I have been recently. They introduced a pyramid with classic methods at the base - ARIMA, GARCH, VEC STS. Then the middle tier was Facebook Prophet  [https://facebook.github.io/prophet/](https://facebook.github.io/prophet/) which I first started using when it was released in 2017. (I recommend reading the paper: Forecasting at Scale: [https://peerj.com/preprints/3190/](https://peerj.com/preprints/3190/)). The top of the pyramid is an RNN - I am guessing AWS means a family of sequence models. My only exposure to RNNs has been in various tutorials - a major downside is the lack of interpretability which most business-cases desire.  One question that came up was How much data do I need for RNNs (LSTM, GRU etc.)? 
3. Amazon Kendra is a really exciting product. It's ostensibly very simple - the combo of search and NLP. My head exploded with applications for Kendra at work  and for various personal projects. 

    **At work:** Could we use Kendra to help make all the disparate docs and wiki's more accessible and queryable?  

    **Personal projects:** Could I use Kendra to make all my online interactions queryable? 

4. Amazon Rekognition is AWS' semi-automated computer vision / classification framework. They have a set of pre-trained models that you can leverage to label your own images and the capacity to build your own datasets and use transfer learning / tuning for custom projects. 

AWS splits image analysis into three categories: Exemplar, Classification and Localization. Exemplar problems use a dataset of specific items you want to identify in other images. Your NN is trained on those images and inference is identifying if the item is present and if so what is the bounding box. A use-case they provide was brand recognition.

Classification - Think of classic MNIST use-cases.

Localization - Where your data includes bounding boxes. 

Another part of the Rekognition stack was how to leverage a positive-feedback loop so that humans-in-the-loop can improve the dataset that is used to train subsequent versions of the model. I thought this was a valuable point because it helps people consider the data-flywheel from the get-go. The first version doesn't need to have awesome F1 score if you have a process to improve the model as it serves inferences! 

Overall, I thought the online conference was a good use of time - It's helpful to see how AWS characterizes these various problem spaces and to see how each of the solutions fits in the ecosystem.
