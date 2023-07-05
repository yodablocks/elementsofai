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
and the other NNNN -> FNFN -> NNFN -> FNFF -> NNNF -> FFNF -> NFNF -> FFFF. 

Intuitively, the strategy is to move the chicken on the other side first, and then go back get either the fox or the feed, and take it to the far side too. The robot then takes the chicken back to the near side to save it from being eaten or from eating the feed, and takes the other remaining object (fox or feed) from the near side to the far side. Finally, the robot goes to fetch the chicken and takes it to the far side to reach the goal.

