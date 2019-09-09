# Quadcopter

This repository contains my results of the project "Teach a quadcopter how to fly", a part of the Machine Learning Engineer Nanodegree at [Udacity](https://www.udacity.com). Using a reinforcement learning approach, an agent was designed and trainined, being able to launch a quadcopter in a continuous space environment.


<details><summary>Table of Contents</summary><p>

* [Content of Repository](#Content)
* [Project Details](#Project_Details)
* [Acknowledgments](#Acknowledgments)

</p></details><p></p>

<a id="Content"></a>
## Content of Repository

- **Quadcopter_Project.ipynb:** A jupyter notebook file with training and results of the project
- **DDPG_Agent.py:** Definition of reinforcement learning agent (following DDPG design)
- **Networks.py:** Definition of actor and critic networks using Keras
- **task.py:** Definiton of environment providing feedback for agent
- **Support.py:** Definition of replay buffer and noise-generation (Ornstein–Uhlenbeck Noise)
- **physics_sim.py:** Simulation of the environment of quadcopter (environment provided by Udacity)

<a id="Project_Details"></a>
## Project Details 

### Network Architechture

The solution implemented is based on the paper [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf) (Lillicrap et al., 2015), a model-free actor-critic algorithm. 

For the network architecture batch normalization and L2-regularizers were used. The actor network has two hidden layers (200,100) as well as the state pathway of the critic network. The action pathway of the critic network has a single hidden layer (100).

Final hyperparameters:
* exploration_mu = 0
* exploration_theta = 0.15
* exploration_sigma = 0.3
* gamma = 0.99
* tau = 0.001


### Reward Function

The goal was to create an algorithm that keeps the quadcopter at an hight of z=100. The action space is limited to providing thrust to the four motors of the quadcopter. A reward function that did solely focus on the postion (x,y,z) of the quadcopter with respect to the desired target position was implemented. Then a hyperbolic tangent was applied to keep the outputs in the intervall [-1,1]:

```Python
reward = np.tanh(1 - 0.003*(abs(self.sim.pose[:3] - self.target_pos))).sum()
```

In the step function however, the z-target was implemented as an aditional condition for ending an episode.<br>
If an episode ends a reward of +10 is implemented:

```Python
if (self.target_pos[2] - self.sim.pose[2]) < 1:
    done = True
if done:
    reward += 10
```

### Results

The algorithm provided comes to a stable solution keeping the quadcopter around z=100, creating a stable reward stream.

**Episode 1-500: Plot of rewards:**
![Rewards](https://github.com/Doc-Ix/quadcopter/blob/master/pictures/quadcopter_rewards.png)

**Episode 1-500: Plot of positions:**
 ![Positions](https://github.com/Doc-Ix/quadcopter/blob/master/pictures/quadcopter_positions.png)

<a id="Acknowledgments"></a>
## Acknowledgments
* The Deep Deterministic Policy Gradients (DDPG) algorithm implemented is based on [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf) (Lillicrap, Timothy P., et al., 2015.).

* Thanks to Udacity for providing this project

* The following sources were very helpful for a deep understanding of the algorithms, the overall concept and its implementation:
  * https://medium.com/@BonsaiAI/deep-reinforcement-learning-models-tips-tricks-for-writing-reward-functions-a84fe525e8e0
  * https://towardsdatascience.com/deep-deterministic-policy-gradients-explained-2d94655a9b7b
  * https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f
  * https://pdfs.semanticscholar.org/400d/9f18a48701c7728c774209867c68f894a573.pdf
  * https://github.com/harshitandro
  * https://github.com/markusbuchholz
  * https://www.youtube.com/playlist?list=PLqYmG7hTraZDM-OYHWgPebj2MfCFzFObQ
  * https://www.youtube.com/watch?v=T0A9voXzhng
