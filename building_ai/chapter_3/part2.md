# II. The nearest neighbor method

## Exercise 15: Vector distances

You are given an array `x_train` with multiple input vectors (the "training data") and another array `x_test` with one more input vector (the "test data"). Find the vector in `x_train` that is most similar to the vector in `x_test`. In other words, find the nearest neighbor of the test data point `x_test`.

The code template gives the function `dist` to calculate the distance between any two vectors. What you need to add is the implementation of the function nearest that takes the arrays `x_train` and `x_test` and prints the index (as an integer between 0, ..., `len(x_train)-1)` of the nearest neighbor.

## My answer:

```
import numpy as np

x_train = np.random.rand(10, 3)   # generate 10 random vectors of dimension 3
x_test = np.random.rand(3)        # generate one more random vector of the same dimension

def dist(a, b):
    sum = 0
    for ai, bi in zip(a, b):
        sum = sum + (ai - bi)**2
    return np.sqrt(sum)
    
def nearest(x_train, x_test):
    nearest = -1
    min_distance = np.Inf
    
    # Loop through all vectors in x_train
    for i, vector in enumerate(x_train):
        # Calculate the distance between the current vector and x_test using the dist function
        distance = dist(vector, x_test)
        
        # Update nearest and min_distance if a closer neighbor is found
        if distance < min_distance:
            nearest = i
            min_distance = distance
    
    print(nearest)

nearest(x_train, x_test)

```

**The answer is correct.**

Here is a short piece of code, using the same cabin pricing data as in the previous section. It uses training data from four cabins to predict the prices of two more cabins in the test data.

```
import math
import numpy as np

x_train = np.array([[25, 2, 50, 1, 500], 
                  [39, 3, 10, 1, 1000],    
                  [82, 5, 20, 2, 120], 
                  [130, 6, 10, 2, 600]])
y_train = [127900, 222100,  268000, 460700]

x_test = np.array([[115, 6, 10, 1, 560], [13, 2, 13, 1, 1000]])


def dist(a, b):
    sum = 0
    for ai, bi in zip(a, b):
        sum = sum + (ai - bi)**2
    return np.sqrt(sum)

n_train = len(x_train) # number of data points in the training set

for test_item in x_test:
    d = np.empty(n_train) # d will hold the distances between this test data point and all the training data points
    for i, train_item in enumerate(x_train):
        d[i] = dist(test_item, train_item)
    nearest_index = np.argmin(d) # the nearest neighbour will be in y_train[nearest]
    print(y_train[nearest_index])

```

## Exercise 16: Nearest neighbor 

In the basic nearest neighbor classifier, the only thing that matters is the class label of the nearest neighbor. But the nearest neighbor may sometimes be noisy or otherwise misleading. Therefore, it may be better to also consider the other nearby data points in addition to the nearest neighbor.

This idea leads us to the so called k-nearest neighbor method, where we consider all the **k** nearest neighbors. If `k=3`, for example, we'd take the three nearest points and choose the class label based on the majority class among them.

The program below uses the library [sklearn](https://scikit-learn.org/) to generate a random dataset. You don't need to be familiar with sklearn, we explain all the necessary information below. Each sample in the dataset has two input features (**X**) and one binary output class (**y**). We can think of a sample as a cabin, with its size and price as its input features, and whether we like it (1) or not (0) as its output class.

The program first generates the random dataset and splits it into training and test sets. Then, for each cabin in the test set, it identifies its nearest neighbor (k=1) from the cabins in the train set using the distance function. However, the program has very high standards and dislikes all the cabins `y_predict[i] = 0`.

Your goal is to make the program smarter by predicting the output class `(y_predict)` for each cabin in the test set based on the majority output class `(y_train)` of its three nearest neighbor (k=3).


*Hint 1:* After calculating all the distances in D (see the code below) you can use [np.argsort](https://stackoverflow.com/q/17901218) to sort the points in increasing distance.

*Hint 2:* You can assume that there are only two possible class labels, 0 and 1. As this is the case, you can get the majority where class by `np.round(np.mean(y))` where `y` is the list containing the class labels of the nearest neighbors. This works by calculating the mean of the class labels and rounding it to zero in case it is less than 0.5 and one otherwise, which is the same as the majority rule.


## My answer:

```
import numpy as np
from sklearn.datasets import make_blobs
from sklearn.preprocessing import MinMaxScaler
from sklearn.model_selection import train_test_split


# create random data with two classes
X, Y = make_blobs(n_samples=16, n_features=2, centers=2, center_box=(-2, 2))

# scale the data so that all values are between 0.0 and 1.0
X = MinMaxScaler().fit_transform(X)

# split two data points from the data as test data and
# use the remaining n-2 points as the training data
X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size=2)

# place-holder for the predicted classes
y_predict = np.empty(len(y_test), dtype=np.int64)

# produce line segments that connect the test data points
# to the nearest neighbors for drawing the chart
lines = []

# distance function
def dist(a, b):
    sum = 0
    for ai, bi in zip(a, b):
        sum = sum + (ai - bi)**2
    return np.sqrt(sum)


def main(X_train, X_test, y_train, y_test):
    global y_predict
    global lines

    k = 3    # classify our test items based on the classes of 3 nearest neighbors

    # process each of the test data points
    for i, test_item in enumerate(X_test):
        # calculate the distances to all training points
        distances = [dist(train_item, test_item) for train_item in X_train]

        # find the indices of the k nearest neighbors
        nearest_indices = np.argsort(distances)[:k]

        # create lines connecting the test point to the k nearest neighbors for the chart
        for idx in nearest_indices:
            lines.append(np.stack((test_item, X_train[idx])))

        # classify the test item based on the majority class among the k nearest neighbors
        k_nearest_classes = y_train[nearest_indices]
        y_predict[i] = np.bincount(k_nearest_classes).argmax()

    print("Predicted classes:")
    print(y_predict)

main(X_train, X_test, y_train, y_test)

```

**The answer is correct.**

