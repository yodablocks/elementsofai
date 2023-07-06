# Chapter 2: Dealing with uncertainty

# I. Probability fundamentals

## Exercise 7: Flip the coin

Write a program that generates 10000 random zeros and ones where the probability of one is p1 and the probability of zero is `1-p1` (hint: `np.random.choice([0,1], p=[1-p1, p1], size=10000)`), counts the number of occurrences of 5 consecutive ones ("11111") in the sequence, and outputs this number as a return value. Check that for `p1` = 2/3, the count is close to 10000 x (2/3)^5 ≈ 1316.9.

## My answer: 

```
import numpy as np

def generate(p1):
    # change this so that it generates 10000 random zeros and ones
    # where the probability of one is p1  
    seq = np.random.choice([0, 1], size=10000, p=[1-p1, p1])
    return seq

def count(seq):
    count = 0
    for i in range(len(seq) - 4): # Adjusted range to account for 5 consecutive elements
        if seq[i:i+5].sum() == 5: 
            count += 1
    return count

def main(p1):
    seq = generate(p1)
    return count(seq)

print(main(2/3))

```
**The answer is correct.**

The probability of "11111" at any given position in the sequence can be calculated as (2/3)^5 ≈ 0.13169. The number of occurrences is close to 10000 times this: 1316.9. To be more precise, the expected number of occurrences is about 0.13169 x 9996 ≈ 1316.3, because there are only 9996 places for a subsequence of length five in a sequence of 10000. The actual number will usually (in fact, with over 99% probability) be somewhere between 1230 and 1404. We check the solution allowing for an even wider margin that covers 99.99% of the cases.


## Exercise 8: Fishing in the Nordics

Suppose we also happen to know the gender of the lottery winner. Here are same OECD statistics as above broken down by gender:

<img width="607" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/4ed17aa8-3128-4f2b-abc6-21e5b424bcdb">

Write a function that uses the above numbers and tries to guess the nationality of the winner when we know that the winner is a fisher and their gender (either female or male).

The argument of the function should be the gender of the winner (**'female'** or **'male'**). The return value of the function should be a pair (**country**, **probability**) where **country** is the most likely nationality of the winner and **probability** is the probability of the country being the nationality of the winner.

*Output Example*

```
if the winner is male, my guess is he's from Finland; probability 08.56%
if the winner is female, my guess is she's from Norway; probability 23.98%
```

**Tip:** Your values might be different, but the formatting should be identical.

**Hint:** Depending on the gender of the winner, you should use the numbers in the "Male fishers" or "Female fishers" column in the above table. The country for which the number in the chosen column is the highest, is the most likely nationality of the winner

## My answer: 

```
countries = ['Denmark', 'Finland', 'Iceland', 'Norway', 'Sweden']
populations = [5615000, 5439000, 324000, 5080000, 9609000]
male_fishers = [1822, 2575, 3400, 11291, 1731]
female_fishers = [69, 77, 400, 320, 26] 

def guess(winner_gender):
    if winner_gender == 'female':
        fishers = female_fishers
    else:
        fishers = male_fishers

    total_fishers = sum(fishers)  # Calculate the total number of fishers based on the given gender
    probabilities = [fisher / total_fishers for fisher in fishers]  # Calculate the probabilities for each country based on the number of fishers
    max_probability = max(probabilities)  # Find the maximum probability
    max_index = probabilities.index(max_probability)  # Find the index of the country with the maximum probability
    guess = countries[max_index]  # Determine the country with the maximum probability
    biggest = max_probability * 100  # Calculate the percentage value of the highest probability

    return (guess, biggest)  # Return the guess and the highest probability percentage


def main():
    country, fraction = guess("male")
    print("if the winner is male, my guess is he's from %s; probability %.2f%%" % (country, fraction))
    country, fraction = guess("female")
    print("if the winner is female, my guess is she's from %s; probability %.2f%%" % (country, fraction))

main()

```
**The answer is correct** 

## 

