# Gomoku AI - Reinforcement Learning (Q-Learning)

This repository contains an AI-powered Gomoku (Five-in-a-Row) game that uses **Q-learning**, a type of reinforcement learning, to train an AI agent capable of playing against human players or other AI agents. The project aims to explore the use of Q-learning to teach an AI to play the game strategically, focusing on winning and blocking moves.

## Game Overview

Gomoku is a strategy board game typically played on a 15x15 grid. The goal is to be the first to align five pieces (either horizontally, vertically, or diagonally). The game has two players: **Player 1** (X) and **Player 2** (AI). The AI is trained using Q-learning, where it learns by playing multiple self-play games, storing state-action-reward transitions, and updating its Q-values.

## Main Architecture

### 1. **Environment (`SimpleGomokuEnv`)**
   - The environment is modeled using a 15x15 grid where each cell represents a position on the board. 
   - The board is initialized as empty, and players (including the AI) take turns placing their marks on the grid.
   - The environment supports methods to:
     - **Reset** the board for a new game.
     - **Step** through each move, calculating rewards and checking for game-ending conditions (win/loss).

### 2. **Agent (`QLearningAgent`)**
   - The AI agent is based on the Q-learning algorithm.
   - The agent maintains a **Q-table** that stores Q-values for state-action pairs. These Q-values represent the expected future rewards for a given state and action.
   - The agent chooses its actions using an **epsilon-greedy policy**, balancing exploration and exploitation.

### 3. **Game Loop**
   - The game alternates between the player's move and the AI's move.
   - After each move, the environment's state is updated, and the agent learns from the reward it receives (based on winning, blocking, or forming a line).
   - The AI updates its Q-table using the rewards and adjusts its policy accordingly.

### 4. **Training Process**
   - The agent is trained over multiple episodes, where each episode represents a new game.
   - The agent learns to improve its strategy by playing against itself (self-play) and adjusting its actions based on the rewards received.
   - After a specified number of episodes, the agent's Q-table is saved and can be loaded for future use.

### 5. **User Interface**
   - The game provides a simple terminal-based interface where players can interact with the AI.
   - The game prints the board after each move, showing the updated grid.
   - The game supports two modes: **Player vs. AI** and **AI vs. AI** for self-play.

## How to Run the Game

To run the game, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/Kotka334/Machine-Learning.git
   cd Gomoku
   ```
2. Install the necessary dependencies:
   ```bash
   pip install numpy
   ```
## Training the AI
To train the AI, you can modify the number of training episodes in the `train_ai()` function. The more episodes the agent plays, the better it gets at the game.
  ```python
  train_ai(agent, env, episodes=2000)
  ```
## User Interface
![Game Screenshot](https://github.com/Kotka334/Machine-Learning/blob/master/GameUI/GameUI.jpg)

## Future Work
- **Deep Learning**: Introduce deep Q-learning to replace the traditional Q-table with a neural network, allowing the AI to generalize better to unseen board states.
- **Monte Carlo Tree Search (MCTS)**: Implement MCTS for better decision-making by simulating possible future moves.
- **Enhanced Game Strategy**: Improve the AI's strategy by introducing more advanced tactics and strategies beyond basic Q-learning.
