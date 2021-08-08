# udacity_drl_colaboration_competition

This repository contains the codes for the project Collaboration and Competition submission.They are

- actor and critic model weights for the two competing actor-critic maddpgs:
    - `checkpoint_actor_0.pth`: first agent actor network
    - `checkpoint_critic_0.pth`: first agent critic network
    - `checkpoint_actor_1.pth`: second agent actor network
    - `checkpoint_critic_1.pth`: second agent critic network
- added maddpg model (`maddpg_agent.py`) 
- actor network and critic networks architectures (`model.py`)
- added tracked training results (time spend training, scores evolution)  **(`INSERT_NAME_HERE.sav`)**
- added the jupyter notebook used to train the agent (`Tennis.ipynb`)

## About the Project

The goal of the project is to train an agent to play Tennis in an environment similar to what is shown in the animation bellow.

![Two trained agents playing the tennis game.](tennis.gif)

To do that a reinforcement learning agent was trained. Specifically it was trained using a Deep Neural Network, with a technique called MADDPG, similar as was presented in the original [MADDPG](https://arxiv.org/pdf/1706.02275v4.pdf) paper.

## What is Reinforcement Learning

From [deepsense.ai](https://deepsense.ai/what-is-reinforcement-learning-the-complete-guide/), we have that 

> Reinforcement learning is the training of machine learning models to make a sequence of decisions. The agent learns to achieve a goal in an uncertain, potentially complex environment. In reinforcement learning, an artificial intelligence faces a game-like situation. The computer employs trial and error to come up with a solution to the problem. To get the machine to do what the programmer wants, the artificial intelligence gets either rewards or penalties for the actions it performs. Its goal is to maximize the total reward.
Although the designer sets the reward policy–that is, the rules of the game–he gives the model no hints or suggestions for how to solve the game. It’s up to the model to figure out how to perform the task to maximize the reward, starting from totally random trials and finishing with sophisticated tactics and superhuman skills. By leveraging the power of search and many trials, reinforcement learning is currently the most effective way to hint machine’s creativity. In contrast to human beings, artificial intelligence can gather experience from thousands of parallel gameplays if a reinforcement learning algorithm is run on a sufficiently powerful computer infrastructure.


## Task Goals and Details

The environment is a **Unity Machine Learning Agents (ML-Agents)**, which is an open-source Unity plugin that enables games and simulations to serve as environments for training intelligent agents. In the tennis environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

**How to complete the task**: the agent must achieve and average score of +0.5 over 100 consecutive episodes.

How the score should be computed for the competitive setting of the tennis environment:

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single score for each episode. That score is the target score that must be at least +0.5 for the task to be solved.

