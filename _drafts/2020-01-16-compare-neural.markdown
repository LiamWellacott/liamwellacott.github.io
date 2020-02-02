---
layout : single
title: "Exploring Biological Neuron Models"
date: 2020-01-16
categories: 
  - Artificial Intelligence
modified: 2020-02-02
description: Analysis of alternative biological/spiking neural network models.
tags: 
  - Spiking Neural Networks
---

*Note:* This blog is for the purpose of increasing my understanding  and organising my thoughts of the topic. I welcome any and all feedback on the technical content, and on the writing style. My email can be found at the bottom of the page. 

# TODO
- Spell check
- Add links for more info
    - For Bio background
    - For ANN background
- Fact check
    - Rosenblatt/Pitt
    - convolution and LSTM understand
- Look into pruning, is it widespread

# Summary

Artificial Neural Networks (ANN) are synonymous with modern AI, and the study of them can be traced almost to the founding of the field. There is a particular dominant abstract model which has been used to produce extremely successful applications (e.g. example in game playing AI and image recognition). I decided to write this to begin to answer the questions: 

- What is omitted in this model?
- What alternative neural models exist? 
- Could there be any advantage to including more biological features in some situations?  

After a brief introduction to the topic of ANN and the underlying biology, I outline two biological or spiking neuron models; Hodgkin-Huxley and Izhikevich. Finally, I describe the possibilities and challenges in using these models in intelligent systems.

*Note*: I assume the reader is familiar with common forms of ANN, since these are better covered by others [elsewhere](TODO), the background is quite light on this topic.

# Background

Nature is abundant with creatures able solve difficult computational problems which so far are yet to be matched by our best science and engineering efforts. The core of this natural intelligence is a network of relatively simple neural cells transmitting information via electrical and chemical signals. From the interactions of these neural cells extraordinarily complex behaviour in the organism emerges. Based on this observation, the study of ANNs attempts to replicate the success of these neural cells in AI systems. 

In the 1950s Rosenblatt introduced the perceptron based on McColough and Pitts 1943 model of the neuron. Using this model, and with significant breakthroughs in training techniques (see backpropagation), perceptrons can be connected and trained to model complex problems effectively. Such networks are typically organised into layers consisting of an input, output, and one or more "hidden layers". This type of network is known as a multi-layer perceptron. Modern deep neural networks have developed significantly beyond multi-layer perceptrons. However, they do share some underlying structural features:

![Fig 1. Perceptron](/assets/img/2020-01-16-compare-neural/basicANN.png){: .align-center}

- **Inputs/Outputs:** Numerical data, beyond the input layer this is the output of other neurons.
- **Weights:** Indicates the strength of the connection between two neurons. The objective of training algorithms is to find the setting of these values which produces the "best" result for some application/problem.
- **Activation:** Function of the weighted sum of the inputs, many alternative functions can be used. However, if using backpropagation in training the function must at least be differentiable.
- **Connection:** Connection is feed-forward. Meaning all connections are to neurons in subsequent layers, there are no lateral or recursive connections. Additionally, neurons are usually fully connected to neurons in the next layer (pruning and layer skipping techniques are exceptions). 
- **Fixed structure:** The number of layers and number of neurons in these layers is fixed, there is no rigorous method for selecting an appropriate structure of neurons for a given problem.

Those familiar with ANNs will not have read anything shocking so far. However, what assumptions have been made about how ANNs ought to function? Do these assumptions hold in all applications to intelligent systems? To begin to answer these questions it is necessary to understand more of what is omitted in this model compared with biological neural cells.

*Note:* The function of natural neurons is a complex biochemical process, which I will not attempt to explain in full here. For a more complete picture of the structure and function of neural cells I found [Neuroscience Online](https://nba.uth.tmc.edu/neuroscience/index.htm) to be a great resource. 

In short, the key method of informational propagation occurs when the potential difference in the cell rises to a critical point known as a threshold, this leads to a further rapid increase in potential difference known as an action potential or "spike" of activity. This action potential is propagated across the cell, which triggers the release of chemical transmitters known as neurotransmitters. These neurotransmitters bind to subsequent neural cells allowing the flow of ions into the cell, which in turn can raise (excite) the potential difference of the cell, possibly leading to the generation of a new action potential. Depending on the neurotransmitter the effect can also be to lower (inhibit) the generation of an action potential.

![Fig 2. Spike example](/assets/img/2020-01-16-compare-neural/Temporal_summation.jfif){: .align-center}

Using the structural features outlined previously we can give examples of how the popular abstract model of the neuron differs greatly from its biological source:

![Fig 3. Biological Neuron](/assets/img/2020-01-16-compare-neural/neuron.png){: .align-center}

- **Inputs/Outputs:** There is clearly no numerical abstraction at the lowest level. inputs and outputs for intermediate neurons (i.e. not sensor/motor neurons) are ultimately chemical neurotransmitters. However, there is also information in the state of chemical concentrations inside the cell (current potential), length of cell, spike timing properties, etc.
- **Weights:** In the model this represents the strength and role (excitatory/inhibitory) of the synaptic connection. In a physical dynamic system there are efficiency limitations and secondary effects. For example the greater the length of the connection the stronger the signal and more time to propagate. The connection strength is thought to increase when a neuron consistently interacts with another (see [Hebbian learning](https://en.wikipedia.org/wiki/Hebbian_theory)).
- **Activation:** Chemicals such as sodium and potassium ions and neurotransmitters are responsible for the generation of action potentials, this occurs in a dynamic system which can be interfered with through other chemicals (recreational and pharmaceutical drugs). Additionally, the time since last activation is an important factor in determining future activation (neurotransmitter resources can be temporarily expended).
- **Connection:** Connection is not constrained to feed-forward (allows recursion) and is not defined prior to learning (according to Hebbian learning). Neural connections display the desirable property of plasticity, which allows for continuous integration of new information.
- **Fixed structure:** The number and layout of the neural cells is also fixed in this case. However, as with all parts of the body, the process of evolution determined the structure of the brain. Neuroscientists have the task of mapping the higher order behaviours to this structure.

## Alternative neuron models

It is not surprising that the model and its biological source are vastly different, after all abstraction is a feature of all models. Again, the question is whether there could be any advantage in including some of the omitted biological features in our neural model, and therefore its worth examining some of the proposed alternatives.

The group of models I will examine are known as biological or spiking neuron models. I will focus on two such models which differ greatly both in biological plausibility and in computational tractability. The key difference of these models when compared to the described ANN is the use of action potential or spikes as the unit of transfer of information (rather than numerical data). One of the implications of this is that timing of activity is crucial to the propagation of information.

Pyhton code implementing these models can be found on [GitHub](https://github.com/LiamWellacott/bio-neuron)

### Hodgkin and Huxley

### Izhikevich

### Networks and Learning

## Conclusion and outlook

- What is omitted in this model?
- What alternative neural models exist? 
- Could there be any advantage to including more biological features in some situations?  

### Problems

- The success of ANN is linked to ease of training, not clear how well this translates?
### What next?

# the bin

The human brain contains in the order of 100 billion neurons each with up to 10,000 connections (neural connectivity representing only part of the mechanisms of the brain).

# TODO
- example of amount of data required
- link to discussion of power imbalance
- Adversarial examples for visual recognition
- example of the jeep recognition?

One of the most apparent gaps between current ANNs and brains is how much data is required for learning. Take the case of visual object recognition, from one encounter of a household cat, we are able to identify cats in a different environment, lighting conditions, and orientations. Additionally, our recognition is robust to different fur patterns, colours, and other major/minor variations (e.g. missing leg like my own cat). An AI system has recently surpassed human ability in visual object recognition using the ImageNet dataset. However, this was only through the collection and application of huge quantities of visual data and processing power. To achieve the desired behaviour, the AI system must learn some generalised principle about the objects which it can then use to recognise the object in unfamiliar circumstances. However, the training process will only make these generalisations if it has to, and if the data set is sufficiently small and there are other properties which can more easily be used for classification it will exploit them.

I believe these factors are part of the explanation of differences in performance between natural and artificial neural networks:
- Raw processing power does not account for intelligence, humans don't have the biggest brains. African elephants have TODO many more neurons than humans. Therefore, the human brain has some internal structures evolved over billions of years. Any attempt at using ANN for intelligent systems must include an attempt to understand how to structure such networks.
- The brain is a work in progress, plastic connections allow for change and adaptation which is not possible with the popular model of ANNs.
- The brain is a program not a function, recursive connections allow for memory, 

To summarise the problems of the current approach:
1. Low data efficiency: Lots of data required to learn generalisable knowledge
2. No recursive connections: means no timing or state representation possible
3. No plasticity: means adapting an ANN to new observations can be extremely difficult


Ideas:
- Using a function which more closely has the characteristics of natural neuron?
- Modelling neural nets as MAS
- The timing may matter in applications such as robotics, an ANN may be produced to perform motor control but if its execution is slow then it will never work, by modelling time directly in the training there is a pressure to shorten control loops in certain conditions
- The problem may not be in the model but in the "blank slate", is this completely the wrong area?