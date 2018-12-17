---
layout: post
title: Reinforcement Learning Note
date: 2018-11-30
tag: AI
---

### Discounted Return
0<= 𝞬 <=1<br>
the agent will only care about if immediate rewards if 𝞬 = 0<br>
the agent will care more about future rewards if 𝞬 is large<br>

### Epsilon-Greedy Policies
0<= ε <=1<br>
the agent selects the greedy action with probability 1- ε <br>
the agent selects an action uniform at random from the set of available(non-greedy AND greedy) actions with probability  ε <br>
so if  ε = 0, the agent always select the greedy action<br>

### Constant-alpha
0<= 𝛼 <=1<br>
If 𝛼 = 0, then the action-value function estimate is never updated by the agent.<br>
If 𝛼 = 1, then the final value estimate for each state-action pair is always equal to the last return that was experienced by the agent (after visiting the pair).<br>
Smaller values for 𝛼 encourage the agent to consider a longer history of returns when calculating the action-value function estimate.<br>
Increasing the value of 𝛼 ensures that the agent focuses more on the most recently sampled returns.<br>
When implementing constant-𝛼 MC control, you must be careful to not set the value of git α too close to 1.<br>
This is because very large values can keep the algorithm from converging to the optimal policy 𝛑∗.<br>
However, you must also be careful to not set the value of 𝛼 too low, as this can result in an agent who learns too slowly.<br>
The best value of 𝛼 for your implementation will greatly depend on your environment and is best gauged through trial-and-error.<br>

### Reading Scientific Papers
As part of this nanodegree, you will learn about many of the most recent, cutting-edge algorithms! Because of this, it will prove useful to learn how to read the original research papers. Here are some excellent tips. Some of the best advice is:
+ Take notes.
+ Read the paper multiple times. On the first couple readings, try to focus on the main points:
    1. What kind of tasks are the authors using deep reinforcement learning (RL) to solve? What are the states, actions, and rewards?
    2. What neural network architecture is used to approximate the action-value function?
    3. How are experience replay and fixed Q-targets used to stabilize the learning algorithm?
    4. What are the results?
+ Understanding the paper will probably take you longer than you think. Be patient, and reach out to the Udacity community with any questions.

### pre-processing steps for FashionMNIST data creation
![pre-processing steps for FashionMNIST data creation](https://yefengjie.github.io/images/res/277ac98f-91ae-4364-8884-0ace482845ea.jpg)

### Best practice to place layers
Best practice is to place any layers whose weights will change during the training process in __init__ and refer to them in the forward function; any layers or functions that always behave in the same way, such as a pre-defined activation function, may appear in the __init__ or in the forward function; it is mostly a matter of style and readability.

### VGG-16 architecture
![VGG-16 architecture](../../../images/res/322fd3e8-9f80-4a69-9b37-3c73e9947f59.jpg)

### Clasisification vs. Regression
The loss function you should choose depends on the kind of CNN you are trying to create; cross entropy is generally good for classification tasks, but you might choose a different loss function for, say, a regression problem that tried to predict (x,y) locations for the center or edges of clothing items instead of class scores.

### Cnn output size
For any convolutional layer, the output feature maps will have the specified depth (a depth of 10 for 10 filters in a convolutional layer) and the dimensions of the produced feature maps (width/height) can be computed as the input image width/height, W, minus the filter size, F, divided by the stride, S, all + 1. The equation looks like: output_dim = (W-F)/S + 1, for an assumed padding size of 0. You can find a derivation of this formula, here.<br>
For a pool layer with a size 2 and stride 2, the output dimension will be reduced by a factor of 2. Read the comments in the code below to see the output size for each layer.