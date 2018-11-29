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