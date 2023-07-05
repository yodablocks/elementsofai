# Naive Bayes classification

## Exercise 12: One word spam filter 

Let's start with a message that only has one word in it: “million”.

## Your task: 

Calculate the **posterior odds** for spam given this word using the table above, starting from prior odds 1:1. Keep in mind that the odds is **not** the same as the probability, which we would usually express as a percentage.

**Give your answer in the form of a single decimal number x.x using the dot '.' as the decimal separator.**

(Remember that odds can be represented as xx:yy or simply as a single decimal number, say z.z (where z.z = xx/yy). You may wish to revisit the discussion on this just before Exercise 9 in Section 3.1 (Odds and Probability).)

## My answer:

**5.1** Correct. As you may have noticed, the structure of this exercise is identical to that of the previous exercise about medical diagnosis. We have the class label spam or ham, and one piece of evidence that we can use to update our prior odds to obtain the posterior odds. We decided above that the prior odds are 1:1. The likelihood ratio is obtained by dividing the probability of the word 'million' in spam divided by the probability of the word 'million' in ham. This we already calculated above, and it can be found in the table of likelihood ratios: the value is 5.1. Now multiply the prior odds by the likelihood ratio to get 1:1 × 5.1 = 5.1. This is the posterior odds. Again, the posterior odds means that for messages that include the word 'million', there are on the average 5.1 spam messages for every ham message. Or to use whole numbers, there are 51 spam messages for every 10 ham messages. The probability value is therefore 51 / (51+10) = 51/61, or approximately 83.6 %.

---

## Exercise 13: Full spam filter 

Now use the naive Bayes method to calculate the posterior odds for spam given the message “million dollars adclick conferences”.

You should again start with the prior odds 1:1, and then multiply the odds repeatedly by the likelihood ratios for each of the four words. Notice that the likelihood ratios are tabulated above for your reference (these are the numbers 5.1, 0.8, and so on).

## Your task: 

Express the result as posterior odds without any rounding of the result. You may take a look at the solution of the previous exercise for help.

## My answer

**65.1168** Correct. We start in the same way as the previous exercise. Multiplying the prior odds by the likelihood ratio 5.1 (for the word 'million') gives posterior odds 5.1. Next we'll simply keep multiplying the odds by the likelihood ratios for the rest of the message. The likelihood ratios can be found in the table above: 0.8 ('dollars'), 53.2 ('adclick'), and 0.3 ('conference'). The product of all these numbers equals 1:1 × 5.1 × 0.8 × 53.2 × 0.3 = 65.1168. This means that for messages that include all these four words, there are on the average about 65 spam messages for each ham message, or about 651 spam messages for every 10 ham messages. If we wanted to get the probability value (which was not asked), it is about 651 / (651+10) = 651 / 661 or approximately 98.5 %. This message would probably end up in your junk mail folder. 

---

# After completing Chapter 3 you should be able to:

+ Express probabilities in terms of natural frequencies
  
+ Apply the Bayes rule to infer risks in simple scenarios

+ Explain the base-rate fallacy and avoid it by applying Bayesian reasoning
