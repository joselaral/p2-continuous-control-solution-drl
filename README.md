# Project 2: Continuous Control

### Solution Results

| Random agent             |  Trained agent |
:-------------------------:|:-------------------------:
![Random Agent](results/20_Reacher_Random_Brain.gif)  |  ![Trained Agent](results/20_Reacher_Trained_Brain.gif)


### Introduction

For this project, you will work with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.


In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Distributed Training

For this project, we will provide you with two separate versions of the Unity environment:
- The first version contains a single agent.
- The second version contains 20 identical agents, each with its own copy of the environment.  

The second version is useful for algorithms like [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience.  

### Solving the Environment

Note that for this project, I decied to solve the second version of the environment, the 20 agent environment.

The barrier for solving the second version of the environment is slightly different, to take into account the presence of many agents.  In particular, your agents must get an average score of +30 (over 100 consecutive episodes, and over all agents).  Specifically,
- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent.  This yields 20 (potentially different) scores.  We then take the average of these 20 scores. 
- This yields an **average score** for each episode (where the average is over all 20 agents).

The environment is considered solved, when the average (over 100 episodes) of those average scores is at least +30. 

### Getting Started

1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:

    - **_Version 2: Twenty (20) Agents_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

2. Place the file in the DRLND GitHub repository, in the `p2_continuous-control-solution-drl/` folder, and unzip (or decompress) the file. 

#### Download & Install Repository


##### Clone repository
```bash
git clone git@github.com:joselaral/p2-continuous-control-solution-drl.git
```

##### Install using Miniconda3
``` bash
cd path/to/p2-continuous-control-solution-drl.git
conda env create -f environment.yml
conda activate drlnd
```

### Repository Content

model.py
- Actor Critic Network model using pytorch library

ddpgagent.py
- Agent that interacts with environment and udpates Neural network weights.

Continuous_Control.ipynb
- Includes the following sections, with Section 4 and 5 guiding users through the solution
1. Start Reacher Environment
2. Examing State and Action Spaces in the Environment
3. Take Random Actions in the Environment
4. It's Your Turn! (Training Solution)
5. Test Trained Agents

results
- videos used to show results at the beginning of this README.md

trained_data
- optimized_weights_ddqn.pth: Trained weights using

P2 Continuous Control.pdf
- Final report

### Assignment Deliverable

Follow the instructions in `Continuous_Control.ipynb` to start working with the environment. Full report included in this repository: P2 Continouous Control.pdf

#### Training Process Notes
I recommend using the 20 Reacher Environment. I attempted to train a DDPG brain using the Reacher environment that only has one agent. However, I wasn't able to train a brain with acceptable average rewards. Shifting to the second training option, I was able to train a brain. 

Follow the recommendations provided by the Udacity mentor in the question I posted: [Why is my Continuous Control agent not reaching +30 average reward?](https://knowledge.udacity.com/questions/855616)