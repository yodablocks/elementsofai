# IV. Overfitting



## Exercise 19: Looking out for overfitting

The program below uses the k-nearest neighbors algorithm. The idea is to not only look at the single nearest training data point (neighbor) but for example the five nearest points, if `k=5`. The normal nearest neighbor classifier amounts to using `k=1`.

Write a program that does the classification for some value of `k` and prints out the training and testing accuracy.

Hint: You can get the model accuracy for a given set using the function `knn.score`.

Try different values of `k` to answer the questions below.

```
from sklearn.neighbors import KNeighborsClassifier
from sklearn.datasets import make_moons
from sklearn.model_selection import train_test_split
import numpy as np

# do not edit this
# create fake data
x, y = make_moons(
    n_samples=500,  # the number of observations
    random_state=42,
    noise=0.3
)
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.33, random_state=42)

# Create a classifier and fit it to our data
knn = KNeighborsClassifier(n_neighbors=133)
knn.fit(x_train, y_train)

print("training accuracy: %f" % 0.0)
print("testing accuracy: %f" % 0.0)

```

<img width="747" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/c8fb2541-d6ad-4fd3-85c0-34918fa71e47">

## What would be a reasonable baseline accuracy your model should outperform in order for it to be considered useful?

**1. 0.5**
2. 0.25
3. any performance that is better than all wrong is enough as a baseline

There are two classes, and the data points are evenly split among them. Assigning every point to either class, or picking a class randomly would result in a 50% accuracy.There are two classes, and the data points are evenly split among them. Assigning every point to either class, or picking a class randomly would result in a 50% accuracy.

## Which of the following values of k do you think was "best"?

1. the choice of k doesn't matter
2. k = 1
3. k = 250
**4. k = 42**
5.  k = 100

## Why ?

1. it gave the lowest training accuracy
2. it gave the highest training accuracy
**3. it gave the highest testing accuracy**
4. it gave the lowest testing accuracy
5. the choice of k doesn't matter

## Is it possible to have a higher test set accuracy than training set accuracy?

**1. Yes**
2. No

It is possible, and for many reasons. For example if you are doing a classification task like here, if your data sets have class imbalance it can easily lead to such a scenario, or if your test set points in this example here would have been picked far away from the decision boundary then they would have been easier to classify correctly than those near the border.

---

## After completing this chapter, you should be able to:

- Use linear regression to make predictions
- Explain how the nearest neighbor method is used for both regression and classification tasks
- Explain the basics of working with text via Natural Language Processing
- Understand the risks of overfitting

*Congratulations for finishing the chapter.*
