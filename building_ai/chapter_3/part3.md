# III. Working with text

## Exercise 17: Bag of words 

Your task is to write a program that calculates the distances (or differences) between every pair of lines in the This Little Piggy rhyme and finds the most similar pair. Use the [Manhattan distance](https://en.wikipedia.org/wiki/Taxicab_geometry) (also called Taxicab distance) as your distance metric.

You can start by building a numpy array to store all the distances. Notice that the diagonal elements in the array (elements at positions `[i, j]` with `i=j`) will be equal to zero. This happens because the program will compare every row also with itself. To avoid selecting those elements, you can assign the value `np.inf` (the maximum possible floating point value). To do this, it's necessary to make sure the type of the array is `float`. Do not use `np.float` to set the type of the array, as it is deprecated. Use Python's built-in type `float` instead.

A quick way to get the index of the element with the lowest value in a 2D array (or in fact, any dimension) is by the function

`np.unravel_index(np.argmin(dist), dist.shape))`

where dist is the 2D array. This will return the index as a list of length two. If you're curious, here's an [intuitive explanation](https://stackoverflow.com/q/48135736) of the function, and here's its [documentation](https://numpy.org/doc/stable/reference/generated/numpy.unravel_index.html).

*Need a Hint:* If you get stuck with the exercise, completing the Beginner and Intermediate level first might help! lol

## My answer: Not easy one... failed few times.

```
import numpy as np

data = [[1, 0, 0, 1, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 1],
        [1, 1, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0, 1],
        [1, 1, 1, 0, 1, 3, 0, 1, 1, 0, 0, 0, 0, 1, 1, 0, 0, 1]]

def dist_manhattan(a, b):
    return np.sum(np.abs(np.array(a) - np.array(b)))

def find_nearest_pair(data):
    N = len(data)
    #print("N: ", N)
    dist = np.empty((N, N), dtype=float)
    dist.fill(np.inf)
    
    for x in range(N):
        for y in range(N):
            if x == y:
                continue
            dist[x, y] = dist_manhattan(data[x], data[y])
 
    print(np.unravel_index(np.argmin(dist), dist.shape))

find_nearest_pair(data)
```

**The answer is correct.**

## Exercise 18: TF-IDF

Let's combine two tasks: finding the most similar pair of lines and the `tf-idf` representation.

Write a program that uses the `tf-idf` vectors to find the most similar pair of lines in a given data set. You can test your solution with the example text below. Note, however, that your solution will be tested on other data sets too, so make sure you don't make use of any special properties of the example data (like there being four lines of text).

This exercise requires a bit more work than average but you should be able to benefit from what you have done in the previous exercises.

## My answer: 

*Hint:* Exercise 17. Bag of Words as well as the other tiers of this exercise explain many relevant concepts in detail. If you're stuck, we would highly recommend you to check them out. When specifying `dtype` for `np.empty`, use `float` instead of `np.float`.

```
import math
import numpy as np

text = '''Humpty Dumpty sat on a wall
Humpty Dumpty had a great fall
all the king's horses and all the king's men
couldn't put Humpty together again'''


def main(text):
    # split the text first into lines and then into lists of words
    docs = [line.split() for line in text.splitlines()]

    N = len(docs)

    # get a list of unique words that appear
    vocabulary = list(set(text.split()))

    df = {}
    tf = {}
    for word in vocabulary:

        tf[word] = [doc.count(word) / len(doc) for doc in docs]

        # (Inverse Document Frequency) df: number of documents containing word
        df[word] = sum([word in doc for doc in docs]) / N

    # loop through documents to calculate the tf-idf values
    tfidf = np.zeros((len(docs), len(vocabulary)))
    for doc_index, doc in enumerate(docs):
        for word_index, word in enumerate(vocabulary):

            value = tf[word][doc_index] * math.log((1 / df[word]), 10)
            tfidf[doc_index][word_index] = value

    print(find_nearest_pair(tfidf))

def find_nearest_pair(data):
    N = len(data)
    dist = np.empty((N, N), dtype=float)
    new_data = all_pairs(data)
    for i in range(len(new_data)):
        for j in range(len(new_data[i])):
            if i == j:
                new_data[i][j] = np.Inf

    return np.unravel_index(np.argmin(new_data), dist.shape)


def distance(row1, row2):
    result = 0
    for i in range(len(row1)):
        result = result + abs(row1[i]-row2[i])
    return result


def all_pairs(data):
    return [[distance(sent1, sent2) for sent1 in data] for sent2 in data]


main(text)
```



