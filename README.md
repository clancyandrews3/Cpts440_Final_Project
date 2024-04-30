# Dots and Boxes Simulator
## Cpts 440 Final Project

## Introduction

This project is a simulator for the game Dots and Boxes, which includes an AI to play against the user. In Dots and Boxes, the board is a grid of dots, and players take turns drawing lines. If a player’s line results in a 1x1 box, they claim the box and take another turn. Once the board is filled, the player with the most boxes wins. The basic strategy is to set up paths of boxes with two lines each, so when one box in the path is completed, the line drawn to claim it serves as the third line to another box, allowing you to claim that as well. You want to force your opponent to give you longer box paths, while giving them small box paths.

## Game Setup

For the simulator aspect, we have a 2d numpy array representing the board. Each position in this 2d array can be a dot, a vertical line, a horizontal line, or a box. Dots are represented by the character “*”. Vertical and horizontal lines are represented by a space if they are unclaimed, they are represented with a “|” or “---”, respectively. If a box is unclaimed, it stores the number of claimed edges it has. If a box is claimed, then it is represented by an “A” for the AI, or a “P” for the human player. The program also keeps track of the list of playable moves, a pair of (row, column) where a line can be drawn. In our case, the user can choose to have a grid size between 2 and 6 boxes.

## Algorithms

For the algorithm, we prepared two simple algorithms to be used for comparison. The “Random” algorithm chooses an available move completely at random. The “Greedy” algorithm claims boxes when they are available, but otherwise chooses moves completely at random. 

The more complex algorithm is based on the minimax algorithm. The traditional minimax algorithm simulates both players' turns by alternating between “maxing” the AI score to represent its own turns, and “mining” the AI score to represent the opposing player’s turn. Our version will differ from typical minimax algorithms, since a player gets an additional turn if they complete a box. These still involve decision points, so they will need to be in different nodes. Because the same player is still playing, we don’t necessarily change whether we are “maxing” or “mining” at each node. In order to improve performance, we imposed a depth limit, so the algorithm will not go beyond a certain number of turns. With larger boards, there are more moves available, so the depth is lower the more moves there are. We use a heuristic function when we reach the depth limit to approximate the score. We also implemented alpha-beta pruning, allowing us to abort a search early if it won’t provide any useful information.

## Algorithm Comparison

By playing against the various AIs, it’s clear that the Minimax algorithm is significantly better than the Random and Greedy algorithms. It is obvious that the Random and Greedy algorithms have some drawbacks, one of which being that they will create most of a box, and then the player can steal the last line and take the point for the box, without the AI taking any preventative measures against the player. The Minimax algorithm doesn’t give you free boxes, unless it has no choice, further showing the improved performance over the Random and Greedy versions. Another example is that if all possible moves would give you boxes, it chooses one that gives you the smallest number of boxes in a row. Additionally, if there are multiple box combos available, it will stop a combo early, in order to force you to claim the last boxes and set up the next box combo for it.

## Conclusion

Having developed and evaluated the performance of the Dots and Boxes simulator with various algorithms, allowing us to understand gameplay strategies, approaches, and algorithm performance. Using the Random and Greedy algorithms as starting benchmarks assisted in further analyzing the Minimax algorithm to determine the necessary methods to increase its performance. The depth limiting and alpha-beta pruning helped in improving the speed at which the Minimax algorithm was able to determine the next move, increasing the ability for faster, more enjoyable gameplay. Additionally, the gameplay improvements that the Minimax algorithm had over the other algorithms allows for the AI in the game to be a worthy opponent. This allows the simulator to be used in many ways, including but not limited to a gameplay trainer or a casual form of entertainment. 

## Authors
Clancy Andrews
Ethan Nelson
Daniel Ochoa
