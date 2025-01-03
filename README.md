# Project details

I completed this guided programming exercise as a part of the Udacity course titled Policy-Based Methods, a component of the Udacity nanodegree titled Deep Reinforcement Learning.

The code in this respository trains an agent (a double-jointed arm) to move to target locations. The environment comprises a 33-dimensional state space and a four-dimensional action space. The state includes the agent's position, rotation, velocity, and angular velocities. The four dimensions of its action correspond to the torques at the two joints. Every entry in the action vector is between -1 and 1. A reward of +0.1 is awarded when the agent's hand transitions to the goal location.

The code trains the agent to maintain its arm at the goal location for as many time steps (transitions) as possible. This learning task is episodic with a maximum number of transitions (time steps) in one episode. The user defines this maximum number and rewards accumulate over an episode to give an episodic score. Alternatively, the user can use the code for distributed training by creating 20 agents, which will explore different parts of the environment (state-action pairs) in parallel. Solving the environment means the trained agent(s) can achieve an average score of at least 30 per agent over 100 consecutive episodes.

# Getting Started

I completed the project in the Project Workspace provided by Udacity. To set up the environment on your own machine, you need to follow the instructions [here](https://github.com/udacity/deep-reinforcement-learning/tree/master/p2_continuous-control#getting-started). They are reproduced here.

1. Clone the Course GitHub repository and set up your Python environment. PyTorch, the ML-Agents toolkit, and a few more Python packages are required to complete the project. These steps can be completed by following the instructions [here](https://github.com/udacity/deep-reinforcement-learning#dependencies).

2. The environment is the Reacher environment ([here](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Learning-Environment-Examples.md#reacher)) on the Unity ML-Agents GitHub page, but you don't need to download/install Unity because the environment can be downloaded from the links below. However, you need to select the link that matches your operating system. If you want to train just one agent, use [Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip), [Mac OSX](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip), [Windows (32-bit)](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip), and [Windows (64-bit)](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip). If you want to train 20 agents, use [Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip), [Mac OSX](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip), [Windows (32-bit)](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip), and [Windows (64-bit)](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip).

3. Place the environment file in the `p2_continuous-control/` directory in the DRLND GitHub repository.
  
4. Unzip (or decompress) the environment file in the directory.

# Instructions

1. First, replace the `Continuous_Control.ipynb` file in the `p2_continuous-control/` directory with the file with the same name in this GitHub repository. Second, download the `ddpg_agent_variant.py` and `model.py` files from this GitHub repository and add them to the `p2_continuous-control/` directory.

2. Open the `Continuous_Control.ipynb` file. It's a Jupyter notebook.

3. The first few sections of the Jupyter notebook are exploratory.

4. In Section four, you train the agent. You can change the hyperparameters by providing different arguments for the function parameters, reproduced here. `n_episodes` is the maximum number of episodes before training ends and `max_t` is the maximum number of time steps (transitions) in one episode. Furthermore, you must comment out one of the two different lines defining `env`, depending on whether you want to train one or two agents.

```
def ddpg(n_episodes=2000, max_t=1000):
```

```
# select this option to load version 1 (with a single agent) of the environment
env = UnityEnvironment(file_name='/data/Reacher_One_Linux_NoVis/Reacher_One_Linux_NoVis.x86_64')

# select this option to load version 2 (with 20 agents) of the environment
env = UnityEnvironment(file_name='/data/Reacher_Linux_NoVis/Reacher.x86_64')
```

5. In the `ddpg_agent_variant.py` file, there are some additional hyperparameters. `LR_ACTOR`, `LR_CRITIC`, and `GAMMA` are the most important three. The first two are the local actor and local critic neural networks' learning rates. `GAMMA` represents the discount factor in the formula used to update a state-action pair's Q value.

# Acknowledgement

I adapted an implementation of DDPG with OpenAI Gym's BipedalWalker environment ([link](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal)) to develop my learning algorithm. I consulted this GitHub repository ([link](https://github.com/gheeraej/Udacity-Continuous-control/tree/master)) when I adapted the algorithm to the configuration with 20 learning agents.
