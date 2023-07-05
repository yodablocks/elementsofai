# The nearest neighbor classifier

## Exercise 14: Customers who bought similar products 

In this exercise, we will build a simple recommendation system for an online shopping application where the users' purchase history is recorded and used to predict which products the user is likely to buy next.

We have data from six users. For each user, we have recorded their recent shopping history of four items and the item they bought after buying these four items: 

<img width="681" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/4a9dab6a-7d42-4669-8b25-68f2e4e31ecf">

The most recent purchase is the one in the rightmost column, so for example, after buying a t-shirt, flip flops, sunglasses, and Moby Dick (novel), Ville bought sunscreen. Our hypothesis is that after buying similar items, other users are also likely to buy sunscreen.

To apply the nearest neighbor method, we need to define what we mean by nearest. This can be done in many different ways, some of which work better than others. Let’s use the shopping history to define the similarity (“nearness”) by counting how many of the items have been purchased by both users.

For example, users Ville and Henrik have both bought a t-shirt, so their similarity is 1. Note that flip flops doesn't count because we don't include the most recent purchase when calculating the similarity — it is reserved for another purpose.

Our task is to predict the next purchase of customer Travis who has bought the following products:

<img width="575" alt="" src="https://github.com/yodablocks/elementsofai/assets/83685559/3f55ba3c-c1cf-4585-b0cc-d47d44c84105">

You can think of Travis being our test data, and the above six users make our training data.

## Proceed as follows:

1. Calculate the similarity of Travis relative to the six users in the training data (done by adding together the number of similar purchases by the users).
2. Having calculated the similarities, identify the user who is most similar to Travis by selecting the largest of the calculated similarities.
3. Predict what Travis is likely to purchase next by looking at the most recent purchase (the rightmost column in the table) of the most similar user from the previous step.

## My answer 

### 1. Who is the user most similar to Travis?

**Ville** Correct. When you calculate the similarities between Travis and all the other users, Ville and Travis will have the largest similarity with a similarity of 3.


### 2. What is the predicted purchase for Travis? 

**Sunscreen** Correct. Since Ville's latest purchase was sunscreen, we will recommend it also to Travis.

---

## Exercise 15: Filter bubbles

As discussed above, recommending news or social media content that a user is likely to click or like, may lead to filter bubbles where the users only see content that is in line with their own values and views.

1. Do you think that filter bubbles are harmful? After all, they are created by recommending content that the user likes. What negative consequences, if any, may be associated with filter bubbles? Feel free to look for more information from other sources.

2. Think of ways to avoid filter bubbles while still being able to recommend content to suit personal preferences. Come up with at least one suggestion. You can look for ideas from other sources, but we'd like to hear your own ideas too!

**Note:** your answer should be at least a few sentences for each part.

**Note:** 
On using ChatGPT and similar models: We appreciate you putting an AI tool into use. Feel free to consult it but note that since we are interested in your own opinion, we expect you to write your final answers yourself.

## My answer:

Filter bubbles can be harmful because they limit exposure to different perspectives, reinforce biases, contribute to echo chambers and misinformation, and lead to societal division and polarization. Despite being based on users' preferences, they can hinder critical thinking and understanding of complex issues. Balancing personalized recommendations with diverse viewpoints is important for a well-rounded and informed society.

One way to avoid filter bubbles while still providing personalized content recommendations is by incorporating a mix of different perspectives. This can be achieved by diversifying the sources of information and including content that challenges the user's existing viewpoints. By intentionally exposing users to a variety of opinions and sources, it helps promote a more balanced understanding of topics. Additionally, users can actively seek out and engage with content from diverse sources themselves, actively expanding their own perspectives and avoiding being confined to a limited bubble of information.
