# III. Hill climbing

## Exercise 3: Reach the highest summit

Let the elevation at each point on the mountain be stored in array h of size 100. The elevation at the leftmost point is thus stored in `h[0]` and the elevation at the rightmost point is stored in `h[99]`.

Here's an example chart. The green box represents Venla's starting position, and the red triangle marks the point where Venla stops. A blue triangle (not shown here) marks the summit.

![1 3-Exercise_3-Reaching_the_highest_summit](https://github.com/yodablocks/elementsofai/assets/83685559/bb452846-e8fc-4ddf-8749-8c3c62535a6f)

The following program starts at a random position and keeps going to the right until Venla can no longer go up. However, perhaps the mountain is a bit rugged which means it's necessary to look a bit further ahead.

Edit the program so that Venla doesn't stop climbing as long as she can go up by moving up to five steps either left or right. If there are multiple choices within five steps that go up, any one of them is good. To check how your climbing algorithm works in action, you can plot the results of your hill climbing using the Plot button. As a reminder, the summit will be marked with a blue triangle.

## My answer:

```
import math
import random             	# just for generating random mountains                                 	 

# generate random mountains                                                                               	 

w = [.05, random.random()/3, random.random()/3]
h = [1.+math.sin(1+x/.6)*w[0]+math.sin(-.3+x/9.)*w[1]+math.sin(-.2+x/30.)*w[2] for x in range(100)]

def climb(x, h):
    # keep climbing until we've found a summit
    summit = False

    # edit here
    while not summit:
        summit = True         # stop unless there's a way up
        if h[x + 1] > h[x]:
            x = x + 1         # right is higher, go there
            summit = False    # and keep going
        else:
            for x_new in range(max(0, x-5), min(99, x+5)):
                if h[x_new] > h[x]:
                    summit = False
                    x = x_new
    return x


def main(h):
    # start at a random place                                                                                  	 
    x0 = random.randint(1, 98)
    x = climb(x0, h)

    return x0, x

main(h)
```

## Example solution

```
def climb(x):
    # keep climbing until we've found a summit
    summit = False

    # edit here
    while not summit:
        summit = True
        for x_new in range(max(0, x-5), min(99, x+5)):
            if h[x_new] > h[x]:
                x = x_new         # here is higher, go here 
                summit = False    # and keep going
    return x
```

## Exercise 4: Probabilities 

Write a program that prints "I love" followed by one word: the additional word should be 'dogs' with 80% probability, 'cats' with 10% probability, and 'bats' with 10% probability.

*Here's an example output:*

```
I love bats
```

## My answer:
```
import random

def main():
    probabilities = [0.8, 0.1, 0.1]
    words = ['dogs', 'cats', 'bats']
    favourite = random.choices(words, probabilities)[0]
    print("I love " + favourite)

main() 
```

## Example solution
```
   import random

   x = random.random()
   if x < 0.8:
      favourite = "dogs"
   elif x < 0.9:
      favourite = "cats"
   else:
      favourite = "bats"
      
   print("I love " + favourite)
```

## Exercise 5: Warm-up Temperature

Suppose the current solution has score S_old = 150 and you try a small modification to create a new solution with score S_new = 140. In the greedy solution, this new solution wouldn't be accepted because it would mean a decrease in the score. In simulated annealing, the new solution is accepted with a certain probability as explained above.

Modify the accept_prob function so that it returns the probability of accepting the new state using simulated annealing. The program should take the two score values (the current and the new) and the temperature value as arguments.


## My answer: 

```
import random
import numpy as np

def accept_prob(S_old, S_new, T):
    # this is the acceptance "probability" in the greedy hill-climbing method
    # where new solutions are accepted if and only if they are better
    # than the old one.
    # change it to be the acceptance probability in simulated annealing

    if S_new > S_old:
        return 1.0
    else:
        return np.exp(-(S_old - S_new) / T)


# the above function will be used as follows. this is shown just for
# your information; you don't have to change anything here
def accept(S_old, S_new, T):
    if random.random() < accept_prob(S_old, S_new, T):
        print(True)
    else:
        print(False)
```

## Example solution

```
import math, random

def accept_prob(S_old, S_new, T):
    if S_new > S_old:
        return 1.0
    else:
        return math.exp((S_new - S_old)/T) # Or analogously, math.exp(-(S_old - S_new)/T)

def accept(S_old, S_new, T):
    if math.random() < accept_prob(S_old, S_new, T):
        return True
    else:
        return False
```

## Exercise 6: Simulated Annealing

Let's use simulated annealing to solve a simple two-dimensional optimization problem. The following code runs 50 optimization tracks in parallel (at the same time). It currently only looks around the current solution and only accepts moves that go up. Modify the program so that it uses simulated annealing.

Remember that the probability of accepting a solution that lowers the score is given by `prob = exp(–(S_old - S_new)/T)`. Remember to also adjust the temperature in a way that it decreases as the simulation goes on, and to handle `T=0` case correctly.

Your goal is to ensure that on the average, at least 30 of the optimization tracks find the global optimum (the highest peak).

If plotting the code takes too long, use this [gist](https://gist.github.com/AayushKucheria/00912c1fe1d60ae01052f0c905c606e2) to plot the code locally on your computer. It should be significantly faster.

## My answer:

```
import numpy as np
import random

N = 100     # size of the problem is N x N                                      
steps = 3000    # total number of iterations                                        
tracks = 50

# generate a landscape with multiple local optima                                          
def generator(x, y, x0=0.0, y0=0.0):
    return np.sin((x/N-x0)*np.pi)+np.sin((y/N-y0)*np.pi)+\
        .07*np.cos(12*(x/N-x0)*np.pi)+.07*np.cos(12*(y/N-y0)*np.pi)

x0 = np.random.random() - 0.5
y0 = np.random.random() - 0.5
h = np.fromfunction(np.vectorize(generator), (N, N), x0=x0, y0=y0, dtype=int)
peak_x, peak_y = np.unravel_index(np.argmax(h), h.shape)

# starting points                                                               
x = np.random.randint(0, N, tracks)
y = np.random.randint(0, N, tracks)

def main():
    global x
    global y

    for step in range(steps):
        # add a temperature schedule here
        T = max(0, ((steps - step)/steps)**3-.005)
        # update solutions on each search track                                     
        for i in range(tracks):
            
            # try a new solution near the current one                               
            x_new = np.random.randint(max(0, x[i]-2), min(N, x[i]+2+1))
            y_new = np.random.randint(max(0, y[i]-2), min(N, y[i]+2+1))
            S_old = h[x[i], y[i]]
            S_new = h[x_new, y_new]

            # change this to use simulated annealing
            if S_new > S_old:
                x[i], y[i] = x_new, y_new   # new solution is better, go there       
            else:
                if random.random() < (np.exp(-(S_old - S_new) / T)):                     # if the new solution is worse, do nothing
                   x[i], y[i] = x_new, y_new  
    # Number of tracks found the peak
    print(sum([x[j] == peak_x and y[j] == peak_y for j in range(tracks)])) 
main()
```

## Nothing...

---

# After completing this chapter, you should be able to:

- Understand what kind of problems can be solved as a straightforward optimization task and explain how simulated annealing can avoid greedy outcomes

- For those who know Python, you will be able to start implementing optimization problems including the use of simulated annealing
