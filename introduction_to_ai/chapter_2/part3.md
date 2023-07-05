# Search and games

## Exercise 7: Why so pessimistic, Max? 

Let's return to the tic-tac-toe game described in the beginning of this section. To narrow down the space of possible end-games to consider, we can observe that Max must clearly place an X on the top row to avoid imminent defeat:

![exercise7-1](https://github.com/yodablocks/elementsofai/assets/83685559/9bb7295a-056b-49ec-97be-d98cc2e9c121)

Now it's Min's turn to play an O. Evaluate the value of this state of the game as well as the other states in the game tree where the above position is the root, using the Minimax algorithm.

## Your task:

Look at the game tree starting from the below board position. Using a pencil and paper, fill in the values of the bottom-level nodes where the game is over. Note that this time some of the games end in a draw, which means that the values of the node is 0 (instead of -1 or 1).

Next continue filling the values of the nodes in the next level up. Since there is no branching at that level, the values on the second-lowest level are the same as at the bottom level.

On the second-highest level, fill in the values by choosing for each node the maximum of the values of the child nodes – as you notice, this is a MAX level. Finally, fill in the root node's value by choosing the minimum of the root node's child nodes' values. This is the value of the game.

**Enter the value of the game as your answer.**

![exercise7-2](https://github.com/yodablocks/elementsofai/assets/83685559/cd6cfbd6-6f9a-4f73-864a-460a86bec98e)

Select the correct answer
+ 1
+ **-1**
+ 0

The value is -1. The values on the second level are 0, 0, and -1. The values on the third level are -1, 0, -1, 0, -1, -1, which are the same as the values on the bottom level. As you can see, Max has all the reason to be serious since by playing in the bottom-right corner, Min can guarantee a win. The inevitable victory of Min can also be seen from the value of the game -1.

---

# After completing Chapter 2 you should be able to:

- Formulate a real-world problem as a search problem

- Formulate a simple game (such as tic-tac-toe) as a game tree

- Use the minimax principle to find optimal moves in a limited-size game tree
