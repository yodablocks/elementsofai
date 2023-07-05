# How neural networks are built

## Exercise 21: Weights and inputs

In this exercise, consider the following expression that has both weights and inputs: 

10.0 + 5.4 × 8 + (-10.2) × 5 + (-0.1) × 22 + 101.4 × (-5) + 0.0 × 2 + 12.0 × (-3) = -543.0

### What is the intercept term in the expression?

a) 543.0
**b) 10.0**
c) -3
d) 5.4?

Correct. The intercept is the number in the equation that is not multiplied by any variable.

### What are the inputs?

**a) 8, 5, 22, -5, 2, -3**
b) 5.4, 8, -10.2, 5, -0.1, 22, 101.4, -5, 0.0, 2, 12.0, -3
c) 5.4, -10.2, -0.1, 101.4, 0.0, 12.0
d) 43.2, -51.0, -2.2, -507.0, 0.0, -36.0

Correct. Compare the equation in the exercise to the one above in the definition: we defined the linear combination to be intercept + weights x inputs, so the inputs are the second numbers in the multiplication.

### Which of the inputs needs to be changed the least to increase the output by a certain amount?

a) first
b) second
c) third
**d) fourth**

Correct. The fourth weight is the largest one. To increase the output by some predetermined amount, the fourth input would have to be increased the least.

### What happens when the fifth input is incremented by one?

**a) nothing**
b) the output increases by one
c) the output increases by two
d) something else

Correct. The weight for the fifth input is 0.0, which means that no matter what value the fifth input has, its effect on the linear combination is always zero.
