# Machine learning 

# I. Linear regression
 
> a + c<sub>1</sub> × x<sub>1</sub> + c<sub>2</sub> × x<sub>2</sub> + c<sub>3</sub> × x<sub>3</sub>

Where "a" is the intercept term.

The purpose of the intercept term is to make it possible to increment (or reduce if the intercept value is negative) the predicted values by a constant amount independently of the inputs.

Below you'll find a simple program that produces predictions about cabin prices. (Disclaimer: The program is meant for demonstration purposes only. Don't blame us if you lose money by trusting its predictions!) You can modify the input values to get predictions for different cabins.

The cabin details, namely size (66m<sup>2</sup>), size of the sauna (5m<sup>2</sup>), distance to water (15m), number of indoor toilets (2) and the proximity of the nearest neighbour (500m) are specified as the elements of the list x. The corresponding coefficients are specified in the list c. The elements of the list x are the inputs  x<sub>1</sub> , ... and x<sub>5</sub> while the elements of c are the coefficients c<sub>1</sub>, ..., c<sub>5</sub> . Note that in this example we don't use the intercept term.


## Exercise 11: Real estate price predictions

Edit the following program so that it can process multiple cabins that may be described by any number of details (like five below), at the same time. You can assume that each of the lists contained in the list x and the coefficients c contain the same number of elements.

```
# input values for three mökkis: size, size of sauna, distance to water, number of indoor bathrooms, 
# proximity of neighbors
X = [[66, 5, 15, 2, 500], 
     [21, 3, 50, 1, 100], 
     [120, 15, 5, 2, 1200]]
c = [3000, 200, -50, 5000, 100]    # coefficient values

def predict(X, c):
    price = 0            
    print(price)

predict(X, c)
```

## My answer:

```
# input values for three mökkis: size, size of sauna, distance to water, number of indoor bathrooms, 
# proximity of neighbors
X = [[66, 5, 15, 2, 500], 
     [21, 3, 50, 1, 100], 
     [120, 15, 5, 2, 1200]]
c = [3000, 200, -50, 5000, 100]    # coefficient values

def predict(X, c):
    for cabin in X:
        prediction = 0
        for xi, ci in zip(cabin, c):
            prediction += xi * ci
        print(prediction)

predict(X, c)
```

**The answer is correct.**

---
```
import numpy as np

x = np.array([66, 5, 15, 2, 500])
c = np.array([3000, 200 , -50, 5000, 100])

print(x @ c)
```

```
import numpy as np

x = np.array([[66, 5, 15, 2, 500], 
              [21, 3, 50, 1, 100]])
c = np.array([3000, 200 , -50, 5000, 100])

print(x @ c)
```
---

## Exercise 12: Least squares

Write a program that calculates the squared error for multiple sets of coefficient values and prints out the index of the set that yields the smallest squared error: this is a poor man's version of the least squares method where we only consider a fixed set of alternative coefficient vectors instead of finding the global optimum.

## My answer:

```
import numpy as np

# data
X = np.array([[66, 5, 15, 2, 500], 
              [21, 3, 50, 1, 100], 
              [120, 15, 5, 2, 1200]])
y = np.array([250000, 60000, 525000])

# alternative sets of coefficient values
c = np.array([[3000, 200 , -50, 5000, 100], 
              [2000, -250, -100, 150, 250], 
              [3000, -100, -150, 0, 150]])   

def find_best(X, y, c):
    smallest_error = np.Inf
    best_index = -1
    for i, coeff in enumerate(c):
        # Calculate the sum of squared errors for the current coefficient set
        predictions = np.dot(X, coeff)
        error = np.sum((y - predictions) ** 2)
        
        # Keep track of the coefficient set yielding the smallest squared error
        if error < smallest_error:
            smallest_error = error
            best_index = i
    print("the best set is set %d" % best_index)


find_best(X, y, c)
```

**The answer is correct.**

## Exercise 13: Predictions with more data

Write a program that reads cabin details and prices from a CSV file (a standard format for tabular data) and fits a linear regression model to it. The program should be able to handle any number of data points (cabins) described by any number of features (like size, size of sauna, number of bathrooms, ...).

You can read a CSV file with the function `np.genfromtxt(datafile, skip_header=1)`. This will return a numpy array that contains the feature data in the columns preceding the last one, and the price data in the last column. The option skip_header=1 just means that the first line in the file is supposed to contain just the column names and shouldn't be included in the actual data.

The output of the program should be the `estimated coefficients` and `the predicted or "fitted" prices` for the same set of cabins used to estimate the parameters. So if you fit the model using data for six cabins with known prices, the program will print out the prices that the model predicts for those six cabins (even if the actual prices are already given in the data).

Note that here we will actually only simulate the file input using Python's io.StringIO function that takes an input string and pretends that the contents is coming from a file. In practice, you would just name the input file that contains the data in the same format as the string input below.

**Hint:** 
You can read the contents of the "file" (or in [this](https://stackoverflow.com/q/24027040) case, the input string) using the `np.genfromtxt` function (check out this stackoverflow answer for help with the dimensionality), and fit the data using `np.linalg.lstsq`. 

## My answer:

```
import numpy as np
from io import StringIO

input_string = '''
25 2 50 1 500 127900
39 3 10 1 1000 222100
13 2 13 1 1000 143750
82 5 20 2 120 268000
130 6 10 2 600 460700
115 6 10 1 550 407000
'''

np.set_printoptions(precision=1)    # this just changes the output settings for easier reading
 
def fit_model(input_file):
    # Read the data from the input file using np.genfromtxt
    data = np.genfromtxt(input_file)

    # Split the data into input features (x) and target values (y)
    x = data[:, :-1]
    y = data[:, -1]

    # Fit the linear regression model using np.linalg.lstsq
    c, _, _, _ = np.linalg.lstsq(x, y, rcond=None)

    print(c)

    # Calculate the predictions using the fitted coefficients
    # predictions = x @ c
    print(x @ c)

# Simulate reading a file
input_file = StringIO(input_string)
fit_model(input_file)

```
