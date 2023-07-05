# The Bayes rule

## Exercise 10: Bayes rule (part 1 of 2) 

Apply the Bayes rule to calculate the **posterior odds for rain** having observed clouds in the morning in Helsinki.

As we calculated above, the prior odds for rain is **206:159** and the likelihood ratio for observing clouds is 9.

Give your result in the form of odds, xx:yy, where xx and yy are numbers. (Note that xx and yy does **not** mean that the numbers should have two digits each.) Remember that when multiplying odds, you should only multiply the numerator (the xx part). For example, if you multiple the odds 5:3 by 5, the result is 25:3. Give the answer without simplifying the expression even if both sides have a common factor.

## My answer:

**1854:159** Correct. The prior odds are 206:159. The likelihood ratio is 9, so we get the posterior odds for rain given clouds to be 9 × 206:159 = 1854:159. So in the long run, on the days when we observe clouds in the morning, we can expect 1854 rainy days for every 159 rainless days, which is about the same as 12 rainy days for one rainless day. If we wanted to express this as a probability (even though this was not the question), we could use the formula x / (x+y) to get the value 1854 / (1854+159) which is about 0.92, or about 92% chance of rain when there are clouds in the morning. Better take an umbrella.

---
## Context for Exercice 11:

## The Bayes rule in practice: breast cancer screening

Our first realistic application is a classical example of using the Bayes rule, namely medical diagnosis. This example also illustrates a common bias in dealing with uncertain information called the base-rate fallacy.

![3_2_bayes-rule-1-3d5328b2a006cca62ed8c54f47be33b1](https://github.com/yodablocks/elementsofai/assets/83685559/d28cba8c-8862-4060-849d-861d8b52c110)

![3_2_bayes-rule-2-2508e993b33b6a7dd06c7644ef8cbd1f](https://github.com/yodablocks/elementsofai/assets/83685559/e6205282-8021-49de-933e-0dd4277de101)

Consider mammographic screening for breast cancer. Using made up percentages for the sake of simplifying the numbers, let’s assume that 5 in 100 women have breast cancer. Suppose that if a person has breast cancer, then the mammograph test will find it 80 times out of 100. When the test comes out suggesting that breast cancer is present, we say that the result is positive, although of course there is nothing positive about this for the person being tested (a technical way of saying this is that the sensitivity of the test is 80%).

The test may also fail in the other direction, namely to indicate breast cancer when none exists. This is called a false positive finding. Suppose that if the person being tested actually doesn’t have breast cancer, the chances that the test nevertheless comes out positive are 10 in 100. (In technical terms, we would say that the specificity of the test is 90%.)

Based on the above probabilities, you are able to calculate the likelihood ratio. You’ll find use for it in the next exercise. If you forgot how the likelihood ratio is calculated, you may wish to check the terminology box earlier in this section and revisit the rain example.

Note: You can use the above diagram with stick figures to validate that your result is in the ballpark (about right) but note that diagram isn’t quite precise. Out of the 95 women who don’t have cancer (the gray figures in the top panel), about nine and a half are expected to get a (false) positive result. The remaining 85 and a half are expected to get a (true) negative result. We didn’t want to be so cruel as to cut people – even stick figures – in half, so we used 9 and 86 as an approximation.

## Exercise 11: Bayes rule (part 2 of 2)

Consider the above breast cancer scenario. An average woman takes the mammograph test and gets a positive test result suggesting breast cancer. What do you think are the odds that she has breast cancer given the observation that the test is positive?

First, use your intuition without applying the Bayes rule, and write down on a piece of paper (not in the answer box below) what you think the chances of having breast cancer are after a positive test result. The intuitive answer will not be a part of your answer. It will be just for your own information.

Next, **calculate the posterior odds for her having breast cancer using the Bayes rule**. This will be your answer.

## Hints:

1. Start by calculating the prior odds.
2. Determine the probability of the observation in case of the event (cancer).
3. Determine the probability of the observation in case of no event (no cancer).
4. Obtain the likelihood ratio as the ratio of the above two probabilities.
5. Finally, multiply the prior odds by the likelihood ratio.

**Enter the posterior odds as your solution below**. Give the answer in the form xx:yy where xx and yy are numbers, without simplifying the expression even if both sides have a common factor.

**40:95** Correct. The prior odds describe the situation before getting the test result. Since five out of 100 women have breast cancer, there is on the average five women with breast cancer for every 95 women without breast cancer, and therefore, the prior odds are 5:95. The likelihood ratio is the probability of a positive result in case of cancer divided by the probability of a positive result in case of no cancer. With the above numbers, this is given by 80/100 divided by 10/100, which is 8. The Bayes rule now gives the posterior odds of breast cancer given the positive test result: posterior odds = 8 × 5:95 = 40:95, which is the correct answer. So despite the positive test result, the odds are actually against the person having breast cancer: among the women who are tested positive, there are on the average 40 women with breast cancer for every 95 women without breast cancer. Note: If we would like to express the chances of breast cancer given the positive test result as a probability (even though this is not what the exercise asked for), we would consider the 40 cases with cancer and the 95 cases without cancer together, and calculate what portion of the total 40 + 95 = 135 individuals have cancer. This gives the result 40 out of 135, or about 30%. This is much higher than the prevalence of breast cancer, 5 in 100, or 5%, but still the chances are that the person has no cancer. If you compare the solution to your intuitive answer, they tend to be quite different for most people. This demonstrates how poorly suited out intuition is for handling uncertain and conflicting information.
