# III. Naive Bayes classifier

The basic idea is to use the Bayes rule to calculate the probability.

`P(spam∣words)=P(words ∣ spam)P(spam)÷P(words)`

This is the probability of a message being spam given the words it contains. If this probability is high, then the filter may automatically delete the message or put it into a junk mail folder.

The idea is to use a large collection of spam messages to estimate the frequency of each word in them, which can be used as P(words ∣ spam). The same is done for non-spam messages, which is often called "ham", to estimate P(words ∣ ham). As you may notice, the Bayes rule formula above doesn't really include the latter term, but it is needed to calculate P(words), which refers to the word frequencies in all messages (either ham or spam).

Processing the words independently leads to a nice procedure where the Bayes rule is applied repeatedly to update the probability each time a new word is received. The procedure is explained in the Introduction to AI, so we'll just skip to the resulting algorithm, which is as follows:

1. Start with the odds 1:1, which means that the probability of spam is 0.5.
2. Calculate the so called likelihood ratio as `r = P(words ∣ spam) ÷ P(words ∣ ham)`
3. Multiply the current odds by r
4. Repeat steps 2 and 3 until all words have been processed

## Exercise 10: Naive Bayes classifier

We have two dice in our desk drawer. One is a normal, plain die with six sides such that each of the sides comes up with equal 1/6 probability. The other one is a loaded die that also has six sides, but that however gives the outcome 6 with every second try on the average, the other five sides being equally probable.

Thus with the first, normal die the probabilities of each side are the same, 0.167 (or 16.7 %). With the second, loaded die, the probability of 6 is 0.5 (or 50 %) and each of the other five sides has probability 0.1 (or 10 %).

The following program gets as its input the choice of the die and then simulates a sequence of ten rolls.

Your task: starting from the odds 1:1, use the naive **Bayes** method to update the odds after each outcome to decide which of the dice is more likely. Edit the function bayes so that it returns True if the most likely die is the loaded one, and False otherwise. Remember to be careful with the indices when accessing list elements!

## My answer:

```
import numpy as np

p1 = [1/6, 1/6, 1/6, 1/6, 1/6, 1/6]   # normal
p2 = [0.1, 0.1, 0.1, 0.1, 0.1, 0.5]   # loaded

def roll(loaded):
    if loaded:
        print("rolling a loaded die")
        p = p2
    else:
        print("rolling a normal die")
        p = p1

    # roll the dice 10 times
    # add 1 to get dice rolls from 1 to 6 instead of 0 to 5
    sequence = np.random.choice(6, size=10, p=p) + 1 
    for roll in sequence:
        print("rolled %d" % roll)
        
    return sequence

def bayes(sequence):
    odds = 1.0           # start with odds 1:1
    for roll in sequence:
        r = p2[roll - 1] / p1[roll - 1]
        odds = odds * r
        #pass             # edit here to update the odds
    if odds > 1:
        return True
    else:
        return False

sequence = roll(True)
if bayes(sequence):
    print("I think loaded")
else:
    print("I think normal")

```

**The answer is correct.**

---

# After completing this chapter, you should be able to:

- Explain probability fundamentals and Monte Carlo method

- Use conditional probability to make inferences

- Use the Bayes rule and Naive Bayes to calculate probability
