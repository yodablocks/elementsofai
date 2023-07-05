# Search and problem solving

## Exercise 5: A smaller rowboat

In the traditional version of this puzzle the robot can only fit one thing on the boat with it. The state space is still the same, but fewer transitions are possible.

**Using the diagram with the possible states below as a starting point, draw the possible transitions in it** (it is MUCH easier to do this with a pencil and paper than without).

Having drawn the state transition diagram, **find the shortest path from NNNN to FFFF, and calculate the number of transitions on it.**

Please type your answer as the **number of transitions in the shortest path** (just a single number like "12"). Do NOT include any further description of your solution. Hint: Do not count the number of states, but the number of transitions. For example, the number of transitions in the path NNNN → FFNF → NFNF → FFFF is 3 instead of 4.

![exercise5](https://github.com/yodablocks/elementsofai/assets/83685559/940884e2-b286-409f-aed2-1c3139e31482)

## My answer:

**7**

Correct. There are two shortest paths that lead from the start NNNN to the goal FFFF. 

One of them is NNNN -> FNFN -> NNFN -> FFFN -> NFNN -> FFNF -> NFNF -> FFFF, 
</br> and the other NNNN -> FNFN -> NNFN -> FNFF -> NNNF -> FFNF -> NFNF -> FFFF. 

Intuitively, the strategy is to move the chicken on the other side first, and then go back get either the fox or the feed, and take it to the far side too. The robot then takes the chicken back to the near side to save it from being eaten or from eating the feed, and takes the other remaining object (fox or feed) from the near side to the far side. Finally, the robot goes to fetch the chicken and takes it to the far side to reach the goal.


## Exercise 6: The Towers of Hanoi

Let's do another puzzle: the well-known Towers of Hanoi. In our version, the puzzle involves three pegs, and two discs: one large, and one small (actually, there can be any number of discs but for the exercise, two is enough to demonstrate the principle).

![exercise6_1](https://github.com/yodablocks/elementsofai/assets/83685559/128b8f98-800e-4049-8965-7b192154b096)

## Your task:

Draw the state diagram. The diagram should include all the nine possible states in the game, connected by lines that show the possible transitions. The picture below shows the overall structure of the state diagram and the positions of the first three states. It shows that from the starting state (at the top corner), you can move to two other states by moving the small disc. Complete the state diagram by placing the remaining states in the correct places. Note that the transitions are again symmetric and you can also move sideways (left or right) or up in the diagram.

After solving the task using pen and paper, enter your solution by choosing which state belongs to which node in the diagram. (Hint: Each state belongs to exactly one node).

![exercise6_2](https://github.com/yodablocks/elementsofai/assets/83685559/77929e7f-aefd-4d9d-8f45-257fbaabfd2e)

Choose for each node (1–6) in the above diagram the correct state A—F from below.

![exercise6_3](https://github.com/yodablocks/elementsofai/assets/83685559/ad886075-0e87-49bb-9873-d9d0e6d382d2)

### What state should be in box 1?

- State A
- State B
- State C
- State D
- **State E**
- State F

### What state should be in box 2?

- State A
- **State B**
- State C
- State D
- State E
- State F
  
### What state should be in box 3?

- State A
- State B
- State C
- State D
- State E
- **State F**

### What state should be in box 4?

- State A
- State B
- State C
- **State D**
- State E
- State F

### What state should be in box 5?

- State A
- State B
- **State C**
- State D
- State E
- State F

### What state should be in box 6?

- **State A**
- State B
- State C
- State D
- State E
- State F

  
