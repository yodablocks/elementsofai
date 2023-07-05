# Why AI matters 

## Exercise 0: Introduction to the Exercises

```
# you can define your own functions
def greet(name):
    print("Welcome " + name + "!")

# go ahead and enter your own name in variable 'name' below to get a warm welcome from us.

def main():
    name = "Emma"
    greet(name)

main()
```

Welcome to your first coding exercise. Please read the instructions in the Intermediate exercise. You can switch between the exercise levels at any time and as many times as you like.

The Advanced exercises differ from the Intermediate ones mainly by the amount of code we provide to start with. In the Intermediate exercises, you are mostly expected to modify a small part of the code, while in the Advanced exercise, you may need to start from scratch.

In all the coding exercises, all the usual tricks apply:

- read the problem statement and the comments in the provided code carefully

- write code in small bits and run often

- feel free to add print statements to see what's going on in the code

- click the test button as many times as needed: the test feedback may help you with debugging

## Note: 
If the code template contains functions, it's important to keep their input and output formats the way they are given. The same applies to print statements in case the program is expected produce printed output.


```
# Solving this exercise will be helpful in the first actual exercise
# (Exercise 1), so consider using this as an opportunity to warm up. 
#
# Your task is the define a function that returns the so called 
# factorial: for any non-negative integer n, the factorial is defined
# as 1 * 2 * ... * n. For example, factorial(5) = 1*2*3*4*5 = 120.
#
# Hint: the simplest way to compute the factorial is to use a
# recursive function, or in other words, a function that calls 
# itself as in 
#     factorial(n) = n * factorial(n-1)
# The recursion should terminate at factorial(0) = 1 so that we
# don't create an infinite loop.

def factorial(n): 
    if n == 0: 
        return 1
    else: 
        return n * factorial(n - 1)  # <-- replace this with the recursive call
        
print(factorial(6))              # this should print 720

```
## The answer is correct - Test cases: 5 / 5

Have a look at the Beginner and Intermediate exercises, if you haven't done so yet. If you run into problems with the exercises, please visit the online community for tips and advice.

Enjoy the course!
