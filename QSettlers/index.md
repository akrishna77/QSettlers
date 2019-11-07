# QSettlers: Deep Reinforcement Learning of Settlers of Catan

## What is Settlers of Catan?

Settlers of Catan is a very popular board game created by Klaus Teuber in 1995 and has been played all over the world for almost 25 years. It is a four-player game that involves rolling dice, collecting resources, and building a settlement that eventually is successful enough to win the game. Although rolling dice and preparing a building strategy is enjoyable, one of the most fun aspects of the game comes from its social component. Throughout the game players negotiate with eachother, proposing trades for various resources and choosing which trades to decline or accept.

From an Artificial Intelligence perspective, developing an agent for this game is an interesting challenge. On one hand, a player must create a building policy to prioritize certain structures in certain locations. On the other hand, a player must utilize the resources of others: only proposing and accepting trades that are most beneficial to the player.

## Current State of the Art

The 'world champion' standard of AI for this board game is a program called [JSettlers](http://nand.net/jsettlers/), developed by [Jeremy Monin](http://www.nand.net/~jeremy/home.htm) over 10 years ago and still in active development today (he gave some advice for this project!). This program is developed in Java and contains a fully-implemented framework of the board game as well as an entirely rule-based agent with hard-coded decisions and heuristics. The existing research surrounding Settlers of Catan use this agent as a benchmark, but no attempts to develop a new Settlers of Catan AI have been able to be significantly better than the JSettlers agent to date.

## The DQN Algorithm

The DQN, or Deep Q-Learning Network, algorithm is a novel approach to reinforcement learning proposed by [the DeepMind team in 2013](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf). As a quick refresher on reinforcement learning, take a look at the graphic below. In a model with an agent and an environment, the goal of reinforcement learning is to develop a policy such that an agent can find itself in a particular state, query its policy, and perform the corresponding action such that its reward is maximized.

| ![Reinforcement Learning Diagram](assets/img/reinforcement.png) | 
|:--:| 
| *Source: https://www.analyticsvidhya.com* |

Q-Learning is a technique to develop such a policy by maintaining a large table with expected rewards (Q values) for every (state, action) pair. The agent will simply look at every action that it can take within a state, and execute the action with the largest Q-value. However, in a large state space with a large amount of possible actions, this table becomes infeasible to keep and thoroughly 'fill out'. 

Deep Q-Learning is an alternative approach to Q-Learning that doesn't face these issues. It involves utilizing a deep neural network to approximate the Q value for (state, action) pairs instead of a table like classical Q-Learning. DQN is very efficient when there is a large state space with a large amount of actions, as it can estimate a Q-value for a never-seen-before state by comparing how similar it is to known states. This algorithm has seen success with game-playing in the context of Atari and Pacman, as opposed to the classical Q-Learning approach. Take a look at the graphic below for a basic representation of these two approaches:

| ![General DQN Diagram](assets/img/Q-Learning.png) | 
|:--:| 
| *Source: https://www.analyticsvidhya.com* |


## Our Goals

Our goal for this project was to use this DQN algorithm to improve upon the JSettlers agent and show that a DQN can be successfully applied to the two game mechanics of Settlers of Catan: building and negotiating. Building an agent that utilizes DQN to play the entire game is outside the scope of this work; we are simply building upon the JSettlers agent by replacing rule-based decisions by DQN output where applicable. 


## DQN Design

As shown in the diagram above, when feeding the 'state' as input

## Architecture Design

A large part of this project was modifying the original JSettlers code to interface with our DQN, which required understanding the underlying architecture of JSettlers and altering it to our needs. The framework of JSettlers is comprised of the following main components:

1. SOCServer: Server that hosts the game and sends messages between clients
2. SOCClient: Player-side client. Connect to a server to play a game.
3. RobotClient: Client to connect an AI to a game; handles messages between Server and Brain.
4. RobotBrain: Contains all the decision-making logic. Takes game state & queries from Client and returns decision.

To implement our own agent, we had to create our own Client and Brain. 


## Training Design

To effectively let the agent play games and learn, we had the following goals:

1. Eliminate the GUI to speed up gameplay
2. Automate the starting of games
3. Automate the recording of game results
4. Eliminate as much latency & communication complexity as possible

We have modified the 

## Results

To do!

## Future Possibilites

A major part of this project was developing the architecture that supports DQN integration with the Settlers of Catan framework. While we applied this reinforcement learning to two mechanics in the game, namely considering offers and choosing preferred settlements to build, in theory every single game decision can be implemented using a DQN with this architecture. Examples of some game decisions that we thought of experimenting with were:

1. Offering Trades
2. Building Roads
3. Time & place to move a robber
4. Investing in Development Cards
5. Targeting specific players in some scenarios

Given enough time and understanding of the game, this project can be extended to create an AI agent completely independant of the JSettlers agent. The results of such an endeavor are unclear, but the possibility is there!
