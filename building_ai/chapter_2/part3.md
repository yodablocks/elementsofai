# III. Naive Bayes classifier

The basic idea is to use the Bayes rule to calculate the probability.

`P(spam∣words)=P(words ∣ spam)P(spam)÷P(words)`

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
