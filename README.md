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

## Environment Set Up

The project environment we're working on with is the [reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. 

**Note:** The Unity ML-Agent team frequently releases updated versions of their environment. I'm are using the v0.4 interface. To avoid any confusion, please use the workspace provided here or work with v0.4 locally.

### Step 1 Clone the DRLND Repository

Clone the [DRLND Repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

### Step 2: Download the Unity Environment

For this project, you will not need to install Unity - this is because the environment is already built for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

2. Place the file in the DRLND GitHub repository, in the `p3_collab-compet/` folder, and unzip (or decompress) the file. 


Also if you are interested in learning to build your own Unity environments after completing the project, you are encouraged to follow the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Getting-Started-with-Balance-Ball.md), which walk you through all of the details of building an environment from a Unity scene. 
