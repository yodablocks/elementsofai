# Optimization

## Exercise 1: Listing pineapple routes

In this exercise you need to list all the possible routes that start from Panama and visit each of the other ports exactly once.

The template code below contains an incomplete **permutations** function which takes as input a specified route and a list of port names absent from that route. Modify the function so that it prints out all the possible orderings of the ports that always begin with Panama (PAN).

The mathematical term for such orderings is a permutation. Note that your program should work for an input **portnames** list of any length. The order in which the permutations are printed doesn't matter.

As the output the function should print each permutation on its own row, as one string, with the port names separated by spaces. For this, you can use the `join` function as follows: `print(' '.join([portnames[i] for i in route]))`.

*Output Example*

```
PAN AMS CAS NYC HEL

...

PAN CAS AMS NYC HEL
```
**Tip:** Your values might be different, but the formatting should be identical.

```
portnames = ["PAN", "AMS", "CAS", "NYC", "HEL"]
 
def permutations(route, ports):
    # Write your recursive code here
    
    # Print the port names in route when the recursion terminates
    print(' '.join([portnames[i] for i in route]))


# This will start the recursion with 0 ("PAN") as the first stop
permutations([0], list(range(1, len(portnames))))

```

## My answer: 

```
portnames = ["PAN", "AMS", "CAS", "NYC", "HEL"]
 
def permutations(route, ports):
    a = 0
    for b in range(1, 5):
        for c in range(1, 5):
            for d in range(1, 5):
                for e in range(1, 5):
                    route = [b, c, d, e]

                    if all(elem in route for elem in ports):
                        route = [a, b, c, d, e]
                        print(' '.join([portnames[i] for i in route]))


# This will start the recursion with 0 ("PAN") as the first stop
permutations([0], list(range(1, len(portnames))))

```

## Example Solution:

```
def permutations(route, ports):
    if len(ports) < 1:
        print(' '.join([portnames[i] for i in route]))
    else:
        for i in range(len(ports)):
            permutations(route+[ports[i]], ports[:i]+ports[i+1:])
 
permutations([0], list(range(1, len(portnames))))
```
