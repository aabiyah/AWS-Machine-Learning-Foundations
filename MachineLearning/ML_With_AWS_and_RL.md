# Introduction to Machine Learning
https://github.com/aabiyah/Introduction-to-Machine-Learning

# Machine Learning with AWS 

## Reinforcement Learning
https://github.com/aabiyah/Introduction-to-Reinforcement-Learning/blob/main/Deep%20dives/Notes.md

Reinforcement learning is used in a variety of fields to solve real-world problems. It’s particularly useful for addressing sequential problems with long-term goals. Let’s take a look at some examples.

### RL is Great at Playing Games
- **Go (board game)** was mastered by the AlphaGo Zero software.
- **Atari classic video games** are commonly used as a learning tool for creating and testing RL software.
- **StarCraft II**, the real-time strategy video game, was mastered by the AlphaStar software.

### RL in Video Game Level Design
- Video game level design determines how complex each stage of a game is and directly affects how boring, frustrating, or fun it is to play that game.
- Video game companies create an agent that plays the game over and over again to collect data that can be visualized on graphs.
- This visual data gives designers a quick way to assess how easy or difficult it is for a player to make progress, which enables them to find that “just right” balance between boredom and frustration faster.

### RL in Wind Energy Optimization
- RL models can also be used to power robotics in physical devices.
- When multiple turbines work together in a wind farm, the turbines in the front, which receive the wind first, can cause poor wind conditions for the turbines behind them. This is called wake turbulence and it reduces the amount of energy that is captured and converted into electrical power.
- Wind energy organizations around the world use reinforcement learning to test solutions. Their models respond to changing wind conditions by changing the angle of the turbine blades. When the upstream turbines slow down, it helps the downstream turbines capture more energy.

### Other Examples of Real-World RL
- Industrial robotics
- Fraud detection
- Stock trading
- Autonomous driving

#### New Terms
1. Agent: The piece of software you are training is called an agent. It makes decisions in an environment to reach a goal.
2. Environment: The environment is the surrounding area with which the agent interacts.
3. Reward: Feedback is given to an agent for each action it takes in a given state. This feedback is a numerical reward.
4. Action: For every state, an agent needs to take an action toward achieving its goal.

## AWS Machine Learning Overview

#### **Why AWS?**
- **Mission:** AWS aims to make machine learning accessible to every developer.
- **Broad and Deep Services:** AWS offers the widest range of AI and ML services with exceptional flexibility.
- **Speed of Development:** With AWS SageMaker, model development that once took months can now be completed in days or weeks.
- **Comprehensive Cloud Offering:** AWS provides a cloud infrastructure optimized for machine learning, hosting more ML activities than any other provider.

#### **AWS Machine Learning Offerings**

**1. AWS AI Services**
   - **Pre-Trained AI Services:** Implement ready-made intelligence for applications such as:
     - Personalized recommendations
     - Modernizing contact centers
     - Enhancing safety and security
     - Boosting customer engagement

**2. Industry-Specific Solutions**
   - **No ML Knowledge Needed:** Apply intelligence to various industries, including healthcare and manufacturing, without needing deep machine learning expertise.

**3. AWS Machine Learning Services**
   - **Amazon SageMaker:** A fully managed service to build, train, and deploy models quickly, simplifying complex ML workflows.

**4. ML Infrastructure and Frameworks**
   - **AWS Workflow Services:** Facilitate management and scaling of ML infrastructure.

#### **Getting Started with AWS ML**

**1. AWS DeepRacer**
   - **Autonomous Race Car:** Tests reinforcement learning models by racing on a physical track.

**2. AWS DeepComposer**
   - **Generative AI Composer:** Creates original melodies and songs.

**3. AWS ML Training and Certification**
   - **Educational Resources:** Provides curriculum for training and certifying developers in machine learning techniques.

> NOTE:
1. Workflow Services: Amazon SageMaker, Deep Learning AMI, Deep Learning Containers, AWS Batch, AWS ParallelCluster, Elastic Kubernetes Service, Elastic Container Service, Amazon EMR
2. Frameworks: TensorFlow, PyTorch, mxnet, Keras, Gluon,
3. Compute, Networking & Storage: EC2 P4 instances, EC2 P3 instances, EC2 G4 instances, EC2 Inf1 instances, Elasric Inference, AWS Outposts, Elastic Fabric Adapter, Amazon S3, Amazon EBS, Amazon FSx, Amazon EFS

### AWS DeepRacer: 
1. https://www.youtube.com/watch?v=li-lJe3QWds
2. https://www.youtube.com/watch?v=90VJxfnfR6c

#### Basic RL Terms
1. Agent
- The piece of software you are training is called an agent.
- It makes decisions in an environment to reach a goal.
- In AWS DeepRacer, the agent is the AWS DeepRacer car, and its goal is to finish * laps around the track as fast as it can while, in some cases, avoiding obstacles.

2. Environment
- The environment is the surrounding area within which our agent interacts.
- For AWS DeepRacer, this is a track in our simulator or in real life.

3. State
- The state is defined by the current position within the environment that is visible, or known, to an agent.
- In AWS DeepRacer’s case, each state is an image captured by its camera.
- The car’s initial state is the starting line of the track and its terminal state is when the car finishes a lap, bumps into an obstacle, or drives off the track.

4. Action
- For every state, an agent needs to take an action toward achieving its goal.
- An AWS DeepRacer car approaching a turn can choose to accelerate or brake and turn left, right, or go straight.

5. Reward
- Feedback is given to an agent for each action it takes in a given state.
- This feedback is a numerical reward.
- A reward function is an incentive plan that assigns scores as rewards to different zones on the track.

6. Episode
- An episode represents a period of trial and error when an agent makes decisions and gets feedback from its environment.
- For AWS DeepRacer, an episode begins at the initial state, when the car leaves the starting position, and ends at the terminal state, when it finishes a lap, bumps into an obstacle, or drives off the track.

In a reinforcement learning model, an agent learns in an interactive real-time environment by trial and error using feedback from its own actions. Feedback is given in the form of rewards.

> Putting Your Spin on AWS DeepRacer: The Practitioner's Role in RL:
## Enhancing AWS DeepRacer Performance

AWS DeepRacer may be autonomous, but you still have an important role to play in the success of your model. In this section, we introduce the training algorithm, action space, hyperparameters, and reward function and discuss how your ideas make a difference.

### Training Algorithm
- An **algorithm** is a set of instructions that tells a computer what to do. Machine Learning (ML) is special because it enables computers to learn without being explicitly programmed.
- The **training algorithm** defines your model’s learning objective, which is to maximize total cumulative reward. Different algorithms have different strategies for achieving this:
  - **Soft Actor-Critic (SAC):** Embraces exploration and is data-efficient but can lack stability.
  - **Proximal Policy Optimization (PPO):** Stable but data-hungry.

### Action Space
- An **action space** is the set of all valid actions, or choices, available to an agent as it interacts with an environment.
  - **Discrete Action Space:** Represents all of an agent's possible actions for each state in a finite set of steering angle and throttle value combinations.
  - **Continuous Action Space:** Allows the agent to select an action from a range of values that you define for each state.

### Hyperparameters
- **Hyperparameters** are variables that control the performance of your agent during training. Experiment with different categories to see how they affect your model.
  - For example, the **learning rate** is a hyperparameter that controls how many new experiences are counted in learning at each step. A higher learning rate results in faster training but may reduce the model’s quality.

### Reward Function
- The **reward function**'s purpose is to encourage the agent to reach its goal. Determining how to reward which actions is one of your most important tasks.

> Putting Reinforcement Learning into Action with AWS DeepRacer
## Visualizing Reward Functions and Trade-Offs in AWS DeepRacer

This video put the concepts we've learned into action by imagining the reward function as a grid mapped over the race track in AWS DeepRacer’s training environment and visualizing it as metrics plotted on a graph. It also introduced the trade-off between exploration and exploitation, an important challenge unique to this type of machine learning.

### Reward Function Grid
- Each square represents a **state**.
- The **green square** is the starting position, or initial state, and the **finish line** is the goal, or terminal state.

#### Key Points about Reward Functions:
- Each state on the grid is assigned a score by your reward function. You incentivize behavior that supports your car’s goal of completing fast laps by giving the highest numbers to the parts of the track on which you want it to drive.
- The reward function is the actual code you'll write to help your agent determine if the action it just took was good or bad, and how good or bad it was.
- The squares containing exes are the track edges and defined as terminal states, which tell your car it has gone off track.

### Exploration vs. Exploitation
- When a car first starts out, it explores by wandering in random directions. However, the more training an agent gets, the more it learns about an environment. This experience helps it become more confident about the actions it chooses.
- **Exploitation** means the car begins to use information from previous experiences to help it reach its goal. Different training algorithms utilize exploration and exploitation differently.

### Reward Graph
- While training your car in the AWS DeepRacer console, your training metrics are displayed on a reward graph.
- Plotting the total reward from each episode allows you to see how the model performs over time. The more reward your car gets, the better your model performs.

### Key Points about AWS DeepRacer
- [AWS DeepRacer](https://example.com) is a combination of a [physical car](https://example.com) and a [virtual simulator](https://example.com) in the [AWS Console](https://example.com), the [AWS DeepRacer League](https://example.com), and [community races](https://example.com).
- An AWS DeepRacer device is not required to start learning: you can start now in the AWS console. The 3D simulator in the AWS console is where training and evaluation take place.

> Exploration versus exploitation: An agent should exploit known information from previous experiences to achieve higher cumulative rewards, but it also needs to explore to gain new experiences that can be used in choosing the best actions in the future.

### Additional Reading
To learn more about AWS AI Services, see [Explore AWS AI services(opens in a new tab).](https://aws.amazon.com/machine-learning/ai-services/?utm_source=Udacity&utm_medium=Webpage&utm_campaign=Udacity%20AWS%20ML%20Foundations%20Course)
To learn more about AWS ML Training and Certification offerings, see [Training and Certification(opens in a new tab).](https://aws.amazon.com/training/?trk=ps_a134p000006vdeTAAQ&trkCampaign=GLBL-FY21-TrainCert-Combined_PaidSearch&sc_channel=PS&sc_campaign=FY21-TrainCert-Combined_PaidSearch&sc_publisher=Google&sc_category=Training%20and%20Certification&sc_country=CA&sc_geo=NAMER&sc_outcome=acq&sc_detail=aws%20training%20and%20certification&sc_content=Generic_exact&sc_matchtype=e&sc_segment=502617786875&sc_medium=TC-P%7CPS-GO%7CBrand%7CDesktop%7CAW%7CTraining%20and%20Certification%7CCombo%7CCA%7CEN%7CText%7Cxx%7CSEM%7CPMO20-00038&s_kwcid=AL!4422!3!502617786875!e!!g!!aws%20training%20and%20certification&s_kwcid=AL!4422!3!502617786875!e!!g!!aws%20training%20and%20certification&ef_id=Cj0KCQjw6-SDBhCMARIsAGbI7UjdXMChuEmUUD2-j8XnYXVklQdsT4KPqYV3lAxL3ww_fQUvs9fGmRoaAkdpEALw_wcB%3AG%3As&utm_source=Udacity&utm_medium=Webpage&utm_campaign=Udacity%20AWS%20ML%20Foundations%20Course)
