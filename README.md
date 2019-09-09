# Quadcopter

This repository contains my results of the project "Teach a quadcopter how to fly", being part of the Machine Learning Engineer Nanodegree at Udacity. The task was to design an agent that is able to fly a quadcopter in a continous space environment, training it with a reinforcement learning algorithm.


<details><summary>Table of Contents</summary><p>

* [Content of Repository](#Content)
* [Project Details](#Project_Details)
* [Acknowledgments](#Acknowledgments)

</p></details><p></p>

<a id="Content"></a>
## Content of Repository

- **Quadcopter_Project.ipynb:** A jupyter notebook file with training and results of the project
- **DDPG_Agent.py:** Definition of reinforcement learning agent using DDPG
- **Networks.py:** Definition of actor and critic networks using Keras
- **task.py:** Definiton of environment providing feedback for agent
- **Support.py:** Definition of replay buffer and noise-generation (Ornstein–Uhlenbeck Noise)
- **physics_sim.py:** Simulation of the environment of quadcopter

<a id="Project_Details"></a>
## Project Details 

### Please post details here
Coming soon...


Hereby the action space is limited to providing thrust to the four motors of the quadcopter.

<a id="Acknowledgments"></a>
## Acknowledgments
* The Deep Deterministic Policy Gradients (DDPG) algorithm implemented is based on Lillicrap, Timothy P., et al., 2015. [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf).

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
