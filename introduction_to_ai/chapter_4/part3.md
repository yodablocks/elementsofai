# Regression

## Exercise 16: Linear regression 

Suppose that an extensive study is carried out, and it is found that in a particular country, the life expectancy (the average number of years that people live) among non-smoking women who don't eat any vegetables is 80 years. Suppose further that on the average, men live 5 years less. Also take the numbers mentioned above: every cigarette per day reduces the life expectancy by half a year, and a handful of veggies per day increases it by one year.

Calculate the life expectancies for the following example cases:

For example, the first case is a male (subtract 5 years), smokes 8 cigarettes per day (subtract 8 × 0.5 = 4 years), and eats two handfuls of veggies per day (add 2 × 1 = 2 years), so the predicted life expectancy is 80 - 5 - 4 + 2 = 73 years.

<img width="680" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/d668adf8-7a9a-4dc4-8b50-9fda18b9a4fe">

## Your task: 
Enter the correct value as an integer (whole number) for the missing sections A, B, and C above.

### A

**81** Correct. A: 80 - 5 + 6 = 81

### B

**73** Correct. 80 - 8 + 1 = 73


### C

**84** Correct. 80 + 4 = 84 

---

## Exercise 17: Life expectancy and education (part 1 of 2)

### Select the correct answer

- It is exactly 64 years

- It is certainly between 60 and 70 years

- It is certainly 70 years or less

- **It is probably less than 90**

Correct. The few data points that we have make it impossible say almost anything about the life expectancy only based on the data. Of course, one can know a great deal about life expectancy from other sources but the data in the above chart is insufficient to do so. The first choice is clearly stating too much. While the intervals in the second and the third choice are likely to be valid, the word 'certainly' makes them unjustified. There is a chance, greater than zero, that the value turns out to be, for example, greater than 70. Thus the only choice that we can be comfortable with is the fourth one.


## Exercise 18: Life expectancy and education (part 2 of 2) 

### Select the correct answer

- Probably between 45 and 50 years

- **Probably between 50 and 90 years**

- Probably between 69 and 71 years

- Probably between 15 and 150 years

The first choice would clearly be an odd estimate since the data strongly suggest that very few countries have life expectancy less than 50, and none of the data points with more than 12 years of education fall below 50. We can't be sure, of course, but life expectancy between 45 and 50 years would in this case be highly unexpected. The second choice is correct because it fits the general trend, and all data points with more than 12 years of education fall within this interval. The interval 69 to 71 years in the third choice could well include the actual value, but based on the above data, it would be too bold to claim to know the outcome with such high accuracy. The interval 15 to 150 years of the fourth choice would almost certainly include the actual value, but we think that it would be a poor summary of what we can learn from the data for the reason that it is too vague.

## Exercise 19: Logistic regression

### Select the correct answer

- 6-7 hours

- 7-8 hours

- 8-9 hours

- **10-11 hours**

Correct. The other answers give roughly a 30%, a 50%, and a 70% chance of passing respectively. To have an 80% chance of passing, you should study for around 10-11 hours.

---

# After completing Chapter 4 you should be able to:

- Explain why machine learning techniques are used

- Distinguish between unsupervised and supervised machine learning scenarios

- Explain the principles of three supervised classification methods: the nearest neighbor method, linear regression, and logistic regression
