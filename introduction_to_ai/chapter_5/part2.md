<img width="663" alt="Screen Shot 2023-07-05 at 6 48 25 PM" src="https://github.com/yodablocks/elementsofai/assets/83685559/4a2ee03f-3177-48d9-b6df-d764d027ba49">
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

---

## Exercise 22: Activations and outputs

Below are graphs for three different activation functions with different properties. First we have the sigmoid function, then the step function, and finally the identity function. IMPORTANT: Note the different y-axis (vertical) scale in the identity function chart.

<img width="632" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/c8733016-edab-46b9-81ab-f78211259d1f">

<img width="655" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/d46cd517-6f26-4820-b402-7cddf8df0480">

<img width="663" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/14d3218f-dc60-4584-a997-b98d45f6cbc5">


### Which of the activations described above gives: the highest output for an input of 5?

- Sigmoid
- Step
- **Identity**

Correct. The identity function will give an output of 5 for an input of 5. The sigmoid will output something very close to 1, and the step function will output exactly 1.

### the lowest output for an input of -5?

- Sigmoid
- Step
- **Identity**

Correct. The identity function will give an output of -5 for an input of -5. The sigmoid will output something very close to 0, and the step function will output exactly 0.

### the highest output for an input of -2.5?

- **Sigmoid**
- Step
- Identity

Correct. For an input of -2.5, the identity function will output -2.5, and the step function will output 0. The sigmoid function will output something that is higher than 0 but lower than 0.1.
