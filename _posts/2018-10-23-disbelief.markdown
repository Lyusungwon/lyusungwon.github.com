---
layout: post
title:  "Large Scale Distributed Deep Networks"
date:   2018-10-23 10:55:59
author: Sungwon Lyu
categories: studies
tags: computer-science distributed-processing
---
## WHY? 
Models with huge number of parameters or huge amount of data do not fit in GPU memory of a machine. 

## WHAT?
This paper introduces DistBelief which is a software framework that enable parallel training in cluster settings. There are two kinds of parallelism in training deep-learning model: Model parallelism and data parallelism. Model parallelism is used when the number of parameters is too large for a machine to train. DistBelief split the parameters into multiple machines and in charge of communication between machines. 

![image](/assets/images/distbelief1.png){: .center-image width="50px"}

Data parallelism is used when dataset is too big or we want to hasten the training. DistBelief provides two kinds of optimization procedures: Downpour SGD and Sandblaster L-BFGS. 

![image](/assets/images/distbelief2.png){: .center-image width="50px"}

Downpour SGD makes a parameter server and multiple replicas of model to multiple machines. Each model in machines accumalate gradient with partitioned set of data. All of the machines send calculated gradient to parameter server and receive updated model every n mini-batch(synchronize). Adaptive optimization such as Adagrad is known to work well with Downpour SGD. Sandblaster L-BFGS implement L-BFGS with a coordinator coordinate the training with messages. 

## So?
Model parallelism was effective to model with larger parameter number. Data parallelism showed faster and better training than single GPU.

## Critic
Suggested framework for distributed deep-learning but lack of theoratical analysis. 

[Dean, Jeffrey, et al. "Large scale distributed deep networks." Advances in neural information processing systems. 2012.](http://papers.nips.cc/paper/4687-large-scale-distributed-deep-networks)