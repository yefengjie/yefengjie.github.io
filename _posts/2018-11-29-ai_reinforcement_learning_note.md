---
layout: post
title: Reinforcement Learning Note
date: 2018-11-29
tag: AI
---

#### Discounted Return
0<=\Gamma<=1<br>
the agent will only care about if immediate rewards if \Gamma=0<br>
the agent will care more about future rewards if /Gamma is large<br>

#### Epsilon-Greedy Policies
0<=\epsilon<=1<br>
the agent selects the greedy action with probability 1-\epsilon<br>
the agent selects an action uniform at random from the set of available(non-greedy AND greedy) actions with probability \epsilon<br>
so if \epsilon=0, the agent always select the greedy action<br>

#### Constant-alpha
0<=alpha<=1<br>
If \alpha = 0, then the action-value function estimate is never updated by the agent.<br>
If \alpha = 1, then the final value estimate for each state-action pair is always equal to the last return that was experienced by the agent (after visiting the pair).<br>
Smaller values for \alpha encourage the agent to consider a longer history of returns when calculating the action-value function estimate.<br>
Increasing the value of \alpha ensures that the agent focuses more on the most recently sampled returns.<br>
When implementing constant-\alpha MC control, you must be careful to not set the value of \alphaα too close to 1.<br>
This is because very large values can keep the algorithm from converging to the optimal policy \pi_*.<br>
However, you must also be careful to not set the value of \alpha too low, as this can result in an agent who learns too slowly.<br>
The best value of \alpha for your implementation will greatly depend on your environment and is best gauged through trial-and-error.<br>