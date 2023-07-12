# I. Logistic regression

## Exercise 20: Logistic regression

You are given a set of three input values and you also have multiple alternative sets of three coefficients. Calculate the predicted output value using the linear formula combined with the logistic activation function.

Do this with all the alternative sets of coefficients. Which of the coefficient sets yields the highest sigmoid output?

```
import math
import numpy as np

x = np.array([4, 3, 0])
c1 = np.array([-.5, .1, .08])
c2 = np.array([-.2, .2, .31])
c3 = np.array([.5, -.1, 2.53])

def sigmoid(z):
    # add your implementation of the sigmoid function here
    print(0)

# calculate the output of the sigmoid for x with all three coefficients

```
## My Answer: 

```
import math
import numpy as np

x = np.array([4, 3, 0])
c1 = np.array([-.5, .1, .08])
c2 = np.array([-.2, .2, .31])
c3 = np.array([.5, -.1, 2.53])

def sigmoid(z):
    return 1 / (1 + math.exp(-z))

# Calculate the output of the sigmoid for x with all three coefficients

sigmoid_output_c1 = sigmoid(np.dot(x, c1))
sigmoid_output_c2 = sigmoid(np.dot(x, c2))
sigmoid_output_c3 = sigmoid(np.dot(x, c3))

print("Sigmoid output for coefficient set c1:", sigmoid_output_c1)
print("Sigmoid output for coefficient set c2:", sigmoid_output_c2)
print("Sigmoid output for coefficient set c3:", sigmoid_output_c3)
```

Output:

Sigmoid output for coefficient set c1: 0.1544652650835347
Sigmoid output for coefficient set c2: 0.45016600268752216
Sigmoid output for coefficient set c3: 0.8455347349164652

From the outputs, we can see that coefficient set c3 yields the highest sigmoid output with a value of 1.0 .

Your answer is correct
