# QSettlers: Deep Reinforcement Learning of Settlers of Catan

## What is Settlers of Catan?

Settlers of Catan is a very popular board game created by Klaus Teuber in 1995 and has been played all over the world for almost 25 years. It is a four-player game that involves rolling dice, collecting resources, and building a settlement that eventually is successful enough to win the game. Although rolling dice and preparing a building strategy is enjoyable, one of the most fun aspects of the game comes from its social component. Throughout the game players negotiate with eachother, proposing trades for various resources and choosing which trades to decline or accept.

From an Artificial Intelligence perspective, developing an agent for this game is an interesting challenge. On one hand, a player must create a building policy to prioritize certain structures in certain locations. On the other hand, a player must utilize the resources of others: only proposing and accepting trades that are most beneficial to the player.

##Current State of the Art

The 'world champion' standard of AI for this board game is a program called JSettlers, developed by Jeremy Monin over 10 years ago and still in active development today (he gave some advice for this project!). This program is developed in Java and is an entirely rule-based agent with hard-coded decisions and heuristics, and the agent comes with a fully-implemented framework of the board game as well. No attempts to develop a new Settlers of Catan AI have been able to be better than the JSettlers agent to date.

##The DQN Algorithm

The DQN, or Deep Q-Learning Network, algorithm is a novel approach to reinforcement learning proposed by [the DeepMind team in 2013](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf). It involves utilizing a deep neural network to approximate the Q value for (state, action) pairs instead of classical Q-Learning, which involves keeping a table with Q values and indexes for every (state, action) pair. DQN is very efficient when there is a large state space with a large amount of actions. In these scenarios, keeping a table for every possible (state, action) pair quickly becomes infeasible.

This algorithm has seen success with game-playing in the context of Atari and Pacman, and generally follows the logic of the diagram below:

<<Insert DQN graphic here>>
