# Machine learning 

# I. Linear regression
 
> a + c<sub>1</sub> × x<sub>1</sub> + c<sub>2</sub> × x<sub>2</sub> + c<sub>3</sub> × x<sub>3</sub>
​
> Where "a" is the intercept term.

The purpose of the intercept term is to make it possible to increment (or reduce if the intercept value is negative) the predicted values by a constant amount independently of the inputs.

Below you'll find a simple program that produces predictions about cabin prices. (Disclaimer: The program is meant for demonstration purposes only. Don't blame us if you lose money by trusting its predictions!) You can modify the input values to get predictions for different cabins.

The cabin details, namely size (66m<sup>2</sup>), size of the sauna (5m<sup>2</sup>), distance to water (15m), number of indoor toilets (2) and the proximity of the nearest neighbour (500m) are specified as the elements of the list x. The corresponding coefficients are specified in the list c. The elements of the list x are the inputs  x<sub>1</sub> , ... and x<sub>5</sub> while the elements of c are the coefficients c<sub>1</sub>, ..., c<sub>5</sub> . Note that in this example we don't use the intercept term.
