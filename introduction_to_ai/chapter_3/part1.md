# Odds and probability

## Exercise 8: Probabilistic forecasts 

For this exercise, remember the key points from the above discussion: probability can be quantified (expressed as a number) and it can be right or wrong. But also keep in mind, that it is usually not possible to draw conclusions about whether a particular number was right or wrong based on a single observation.

Consider the following four probabilistic forecasts and outcomes. What can we conclude based on the outcome about the correctness of the forecasts? Can we conclude that the probability given by the forecast was indeed the correct probability (choose "right"), that the forecast was wrong (choose "wrong"), or can we conclude neither way (choose "cannot be concluded")?

### The weather forecast says it's going to rain with 90% probability tomorrow but the day turns out to be all sun and no rain.

- Right
- Wrong
- **Cannot be concluded**

We can't conclude that the weather forecast was wrong based on only the single event. The forecast said it's going to rain with 90% probability, which means it would not rain with 10% probability or in one out of 10 days. It is perfectly plausible that the day in question was the 1 in 10 event. Concluding that the probability 90% was correct would also be wrong because by the same argument, we could then conclude that 80% chance of rain was also correct, and both cannot be correct at the same time.

### The weather forecast says it's going to rain with 0% probability tomorrow but the day turns out to be rainy.

- Right
- **Wrong**
- Cannot be concluded

The weather forecast was wrong because a 0% probability means that it should definitely not rain. But it did.

### Suppose you monitor a weather forecaster for a long time. You only consider the days for which the forecast gives 80% chance of rain. You find that in the long run, on the average it rains on three out of every five days.

- Right
- **Wrong**
- Cannot be concluded

The weather forecasts are wrong if they predict 80% chance of rain and it rains only 60% (three out of five) of the time in the long run. (Note that we'd really need to keep track of the accuracy for a long time to reach this conclusion but that's what "in the long run" means.) In practice, weather forecasters actually tend to provide this kind of 'wrong' predictions just to be safe: people are often quite disappointed when the weather turns out to be worse than predicted but pleasantly surprised when it turns out better than predicted.

### In the United States presidential election 2016, a well-known political forecast blog, Five-Thirty-Eight, gave Clinton a 71.4% chance of winning (vs Trump's 28.6%). However, contrary to the prediction, Donald Trump was elected the 45th president of the United States.

- Right
- Wrong
- **Cannot be concluded**

Cannot be concluded to be wrong (or right). Sometimes unlikely things happen. Considering the previous item, it would actually have been wrong to predict, say, 90% or 100% chance for Trump if there simply isn't enough information available to anticipate the outcome. In other words, perhaps Trump's victory was a rare (or rareish) event with 28.6% probability. Such events are expected to happen in more than one out of four cases, after all.

---

## Exercise 9: Odds

As we already mentioned above, the odds 3:1 – for example three rainy days for each rainless day – corresponds to probability 0.75 (or in percentages 75%).

In general, if the odds in favor of an event are x:y, the probability of the event is given by x / (x+y). Try that with the odds 3:1 if you like. You should get the answer 0.75.

As we also pointed out, the odds 6:2 corresponds to exactly the same probability as the odds 3:1 because when we let x=6 and y=2, and write them in the formula x / (x+y), we get 6/(6+2), which comes out as 6/8 = 3/4 = 0.75.

## Your task:

**For the first three items 1–3**, convert from odds to probabilities expressed as natural frequencies; for example from 1:1 to 1/2. Give your answer as a fraction, for example 2/3.

**For the last three items 4–6**, convert the odds into probabilities expressed as percentages (e.g. 4.2%). Give your answer in percentages using a single decimal, for example 12.2%.

Hint: the calculations are to be calculated with a simple calculator and the formulas can be found above.


### 1. The odds for getting three of a kind in poker are about 1:46.

**1/47**
Correct. There are 46 situations where you do not get three of a kind for one where you get it, so the probability is 1/(1+46) = 1/47.

### 2. The odds for rain in Helsinki are 206:159.

**206/365**
Correct. There are 206 rainy days for 159 dry days, so the probability is 206/(206+159) = 206/365.

### 3. The odds for rain in San Diego are 23:342.

**23/365**
Correct. There are 23 rainy days for 342 dry days, so the probability is 23/(23+342) = 23/365.

---

### 4. The odds for getting three of a kind in poker are about 1:46.

**2.1%**
Correct. Previously we had the probability as 1/(1+ 46) = 1/47, which gives us roughly 0.0213, which rounds to 2.1%.

### 5. The odds for rain in Helsinki are 206:159.

**56.4%**
Correct. Previously we had the probability as 206/(206 + 159) = 206/365, which gives us roughly 0.5644, which rounds to 56.4%.

### 6. The odds for rain in San Diego are 23:342.

**6.3%**
Correct. Previously we had the probability as 23/(23 + 342) = 23/365, which gives us roughly 0.0630, which rounds to 6.3%.

