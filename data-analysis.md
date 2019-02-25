## Data Analysis (27 questions)

#### 1. (Given a Dataset) Analyze this dataset and tell me what you can learn from it.
#### 2. What is R2? What are some other metrics that could be better than R2 and why?
  - goodness of fit measure. variance explained by the regression / total variance
  - the more predictors you add the higher R^2 becomes.
    - hence use adjusted R^2 which adjusts for the degrees of freedom 
    - or train error metrics
#### 3. What is the curse of dimensionality?
  - In general, high dimension data makes many algorithm slow to run.
  - High dimensionality makes clustering hard, because having lots of dimensions means that everything is "far away" from each other.
  - To cover enough variation of the data, we need to capture a very wide range for each variable as the number of variables increases.
  - All samples are close to the edge of the sample. And this is a bad news because prediction is much more difficult near the edges of the training sample.
  - The sampling density decreases exponentially as p increases and hence the data becomes much more sparse without significantly more data. 
#### 4. Is more data always better?
  - Statistically,
    - It depends on the quality of your data, for example, if your data is biased, just getting more data won’t help.
    - It depends on your model. If your model suffers from high bias, getting more data won’t improve your test results beyond a point. You’d need to add more features, etc.
  - Practically,
    - Also there’s a tradeoff between having more data and the additional storage, computational power, memory it requires. Hence, always think about the cost of having more data.
#### 5. What are advantages of plotting your data before performing analysis?
  - get some sense of the data. So some easy to spot pattern can be found easily.
  - Data sets have errors.  You won't find them all but you might find some. That 212 year old man. That 9 foot tall woman.  
  - Variables can have strange distributions, outliers, etc.
    - Variables can be multimodal.
#### 6. How can you make sure that you don’t analyze something that ends up meaningless?
  - Make sure your data is not rubbish.
    - Experiments must be clean or have proper controls.
  - Understand the data generating process.
  - Figure out some plausible stroies behind the data.
  - Proper exploratory data analysis.  
  - Remember a proper null result != meaningless.
#### 7. What is the role of trial and error in data analysis? What is the the role of making a hypothesis before diving in?
  - data analysis is a repetition of setting up a new hypothesis and trying to refute the null hypothesis.
  - The scientific method is eminently inductive: we elaborate a hypothesis, test it and refute it or not. As a result, we come up with new hypotheses which are in turn tested and so on. This is an iterative process.
  - For ML jobs, trial and error lets you know which model fits the data better.
#### 8. How can you determine which features are the most important in your model?
  - Feature importance plot (check feature correlation first, PCA if high correlation)
  - things like LIME
  - Look at performance gain/ loss in forward/ backward variable selection 
#### 9. How do you deal with some of your predictors being missing?
  - Values are missing completely at random:
    - Remove rows with missing values, especially if you don't lose too much of the dataset after doing so.
  - Values are missing at random:
    - Imputation: depends on your data, kNN, median, mean, etc.
    - For inference, use multiple imputation instead otherwise your SE would be messed up.
  - Values are not missing at random:
    - Being missing is informative: can be treated as another category for categorical variables and put to 0 (or whatever constant value) and add a dummy to indicate missing.
#### 10. You have several variables that are positively correlated with your response, and you think combining all of the variables could give you a good prediction of your response. However, you see that in the multiple linear regression, one of the weights on the predictors is negative. What could be the issue?
  - Multicollinearity refers to a situation in which two or more explanatory variables in a multiple regression model are highly linearly correlated. 
  - Leave the model as is, despite multicollinearity. The presence of multicollinearity doesn't affect the efficiency of extrapolating the fitted model to new data provided that the predictor variables follow the same pattern of multicollinearity in the new data as in the data on which the regression model is based.
    - Assuming you only care about prediction
  - principal component regression
#### 11. Let’s say you’re given an unfeasible amount of predictors in a predictive modeling task. What are some ways to make the prediction more feasible?
  - think through the data generating process. drop all the variables that should not have any effect.
  - If possible, combine some variables to a new variable through some math transformation.
  - PCA or similar dimension reduction technique
#### 12. Now you have a feasible amount of predictors, but you’re fairly sure that you don’t need all of them. How would you perform feature selection on the dataset?
  - lasso / elastic net regression
  - Univariate Feature Selection where a statistical test is applied to each feature individually. You retain only the best features according to the test outcome scores
  - Recursive Feature Elimination:  
    - First, train a model with all the feature and evaluate its performance on held out data.
    - Then drop let say the 10% weakest features (e.g. the feature with least absolute coefficients in a linear model) and retrain on the remaining features.
    - Iterate until you observe a sharp drop in the predictive accuracy of the model.
#### 13. Your linear regression didn’t run and communicates that there are an infinite number of best estimates for the regression coefficients. What could be wrong?
  - feature number > data points
  - If some of the explanatory variables are perfectly correlated then the coefficients would not be unique. 
#### 14. You run your regression on different subsets of your data, and find that in each subset, the beta value for a certain variable varies wildly. What could be the issue here?
  - Model is overfitting.
  - The dataset might be heterogeneous. In which case, it is recommended to cluster datasets into different subsets wisely, and then do a hierarchical model. Or, use models like non parametric models (trees) which can deal with heterogeneity quite nicely.
#### 15. What is the main idea behind ensemble learning? If I had many different models that predicted the same response variable, what might I want to do to incorporate all of the models? Would you expect this to perform better than an individual model or worse?
  - The assumption is that a group of weak learners can be combined to form a strong learner.
  - Hence the combined model is expected to perform better than an individual model.
  - Assumptions:
    - average out biases
    - reduce variance
  - Bagging works because some underlying learning algorithms are unstable: slightly different inputs leads to very different outputs. If you can take advantage of this instability by running multiple instances, it can be shown that the reduced instability leads to lower error. If you want to understand why, the original bagging paper( [http://www.springerlink.com/cont...](http://www.springerlink.com/content/l4780124w2874025/)) has a section called "why bagging works"
  - Boosting works because of the focus on better defining the "decision edge". By reweighting examples near the margin (the positive and negative examples) you get a reduced error (see http://citeseerx.ist.psu.edu/vie...)
  - Use the outputs of your models as inputs to a meta-model.   

For example, if you're doing binary classification, you can use all the probability outputs of your individual models as inputs to a final logistic regression (or any model, really) that can combine the probability estimates.  

One very important point is to make sure that the output of your models are out-of-sample predictions. This means that the predicted value for any row in your dataframe should NOT depend on the actual value for that row.
#### 16. Given that you have wifi data in your office, how would you determine which rooms and areas are underutilized and overutilized?
  - If wifi is used more (overloaded) in one room, then that one is over utilized! Maybe account for the room capacity and normalize the data.
#### 17. How could you use GPS data from a car to determine the quality of a driver?
  - What is the quality of a driver?
#### 18. Given accelerometer, altitude, and fuel usage data from a car, how would you determine the optimum acceleration pattern to drive over hills?
  - Dynamic programing if road condition is available. RL if not?
#### 19. Given position data of NBA players in a season’s games, how would you evaluate a basketball player’s defensive ability?
  - Since we only have position data, I think we need to assume players and coaches know what they're doing: assign high defensive points to players that occupy defensive positions.
  - somehow estimate a game?
#### 20. How would you quantify the influence of a Twitter user?
  - like page rank with each user corresponding to the webpages and linking to the page equivalent to following.
#### 21. Given location data of golf balls in games, how would construct a model that can advise golfers where to aim?
#### 22. You have 100 mathletes and 100 math problems. Each mathlete gets to choose 10 problems to solve. Given data on who got what problem correct, how would you rank the problems in terms of difficulty?
  - One way you could do this is by storing a "skill level" for each user and a "difficulty level" for each problem.  We assume that the probability that a user solves a problem only depends on the skill of the user and the difficulty of the problem.*  Then we maximize the likelihood of the data to find the hidden skill and difficulty levels.
  - The Rasch model for dichotomous data takes the form:  
{\displaystyle \Pr\\{X_{ni}=1\\}={\frac {\exp({\beta _{n}}-{\delta _{i}})}{1+\exp({\beta _{n}}-{\delta _{i}})}},}  
where  is the ability of person  and  is the difficulty of item}.
#### 23. You have 5000 people that rank 10 sushis in terms of saltiness. How would you aggregate this data to estimate the true saltiness rank in each sushi?
  - If each person tastes all 10 sushis, then something like ideal point estimation would work.
  - If they get to choose which sushi to eat, probably we need to consider some sort of selection model.
#### 24. Given data on congressional bills and which congressional representatives co-sponsored the bills, how would you determine which other representatives are most similar to yours in voting behavior? How would you evaluate who is the most liberal? Most republican? Most bipartisan?
  - classical ideal point estimation
#### 25. How would you come up with an algorithm to detect plagiarism in online content?
  - reduce the text to a more compact form (e.g. fingerprinting, bag of words) then compare those with other texts by calculating the similarity
#### 26. You have data on all purchases of customers at a grocery store. Describe to me how you would program an algorithm that would cluster the customers into groups. How would you determine the appropriate number of clusters to include?
  - try different classifical clustering methods
  - choose a small value of k that still has a low SSE (elbow method)
  - <https://bl.ocks.org/rpgove/0060ff3b656618e9136b>
  - see if the clustering result makes sense
#### 27. Let's say you're building the recommended music engine at Spotify to recommend people music based on past listening history. How would you approach this problem?
  - [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering)
  - something like ideal point estimation
