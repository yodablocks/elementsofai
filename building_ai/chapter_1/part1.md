# II. Optimization

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


## Exercise 2: Pineapple route emissions

Building on the previous solution, modify the code so that it finds the route with minimum carbon emissions and prints it out. Again, the program should work for any number of ports. You can assume that the distances between the ports are given in an array of the appropriate size so that the distance between ports i and j is found in D[i][j].

*Output Example*

```
PAN AMS CAS NYC HEL 240.1 kg
```
**Tip:** Your values might be different, but the formatting should be identical.

## My answer

```
portnames = ["PAN", "AMS", "CAS", "NYC", "HEL"]

D = [
    [0, 8943, 8019, 3652, 10545],
    [8943, 0, 2619, 6317, 2078],
    [8019, 2619, 0, 5836, 4939],
    [3652, 6317, 5836, 0, 7825],
    [10545, 2078, 4939, 7825, 0]
]

# assume 20g per km per metric ton (of pineapples)
co2 = 0.020

# DATA BLOCK ENDS

# these variables are initialized to nonsensical values
# your program should determine the correct values for them
smallest = 1000000
bestroute = [0, 0, 0, 0, 0]

def permutations(route, ports):
    global smallest, bestroute 

    # Base case: If there are no more ports to visit,
    # calculate the emissions and update the smallest and bestroute if necessary
    if not ports:
        emissions = calculate_emissions(route)
        if emissions < smallest:
            smallest = emissions
            bestroute = route
        return

    # Recursive case: Visit each remaining port and make a recursive call
    for port in ports:
        new_route = route + [port]
        new_ports = ports.copy()
        new_ports.remove(port)
        permutations(new_route, new_ports)

def calculate_emissions(route):
    emissions = 0.0
    for i in range(len(route) - 1):
        start_port = route[i]
        end_port = route[i + 1]
        emissions += D[start_port][end_port] * co2
    return emissions

def main():
    # Do not edit any (global) variables using this function, as it will mess up the testing

    # This will start the recursion
    permutations([0], list(range(1, len(portnames))))

    # Print the best route and its emissions
    print(' '.join([portnames[i] for i in bestroute]) + " %.1f kg" % smallest)

main()

```

## Example solution

```
portnames = ["PAN", "AMS", "CAS", "NYC", "HEL"]

D = [
        [0,8943,8019,3652,10545],
        [8943,0,2619,6317,2078],
        [8019,2619,0,5836,4939],
        [3652,6317,5836,0,7825],
        [10545,2078,4939,7825,0]
    ]

co2 = 0.020

smallest = 1000000
bestroute = None

def permutations(route, ports):
    global smallest, bestroute
    if len(ports) < 1:
        score = co2 * sum(D[i][j] for i, j in zip(route[:-1], route[1:]))
        if score < smallest:
            smallest = score
            bestroute = route
    else:
        for i in range(len(ports)):
            permutations(route+[ports[i]], ports[:i]+ports[i+1:])

def main():
    permutations([0], list(range(1, len(portnames))))

    print(' '.join([portnames[i] for i in bestroute]) + " %.1f kg" % smallest)

main()

```
