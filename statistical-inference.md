## Statistical Inference (15 questions)

#### 1. In an A/B test, how can you check if assignment to the various buckets was truly random?
  - Plot the distributions of multiple features for both A and B and make sure that they have the same shape. More rigorously, we can conduct a permutation test to see if the distributions are the same.
  - MANOVA to compare different means
  - chi-squared test of independence
#### 2. What might be the benefits of running an A/A test, where you have two buckets who are exposed to the exact same product?
  - Verify the sampling algorithm is random.
  - <https://www.dynamicyield.com/glossary/aa-testing/>
#### 3. What would be the hazards of letting users sneak a peek at the other bucket in an A/B test?
  - Users may choose a better one, lead to confounders.
  - The user might not act the same way had they not seen the other bucket. 
  - So clustering wisely.
#### 4. What would be some issues if blogs decide to cover one of your experimental groups?
  - Same as the previous question. The above problem can happen in larger scale.
#### 5. How would you conduct an A/B test on an opt-in feature? 
  - Create an IV at the opt-in stage, like the classic lottery scheme. RDD if opt-in is decided by a sharp curoff (queue model to assign opt-in feature). diff in diff if we know they follow the same trend.
#### 6. How would you run an A/B test for many variants, say 20 or more?
  - one control, 20 treatment, if the sample size for each group is big enough.
  - Ways to attempt to correct for this include changing your confidence level (e.g. Bonferroni Correction) or doing family-wide tests before you dive in to the individual metrics (e.g. Fisher's Protected LSD).
#### 7. How would you run an A/B test if the observations are extremely right-skewed?
  - ignore when appropriate
  - lower the variability by modifying the KPI
  - cap values
  - percentile metrics
  - log transform
  - <https://www.quora.com/How-would-you-run-an-A-B-test-if-the-observations-are-extremely-right-skewed>
#### 8. I have two different experiments that both change the sign-up button to my website. I want to test them at the same time. What kinds of things should I keep in mind?
  - exclusive -> ok
#### 9. What is a p-value? What is the difference between type-1 and type-2 error?
  - see previous questions.  
  - type-1 error: rejecting Ho when Ho is true
  - type-2 error: not rejecting Ho when Ha is true
#### 10. You are AirBnB and you want to test the hypothesis that a greater number of photographs increases the chances that a buyer selects the listing. How would you test this hypothesis?
  - Need to figure out does the client want a causal relationship or description relationship.
  - For causal relationship, we can run a blocked experiment:
    - try to match treatment and control closely. Randomly remove/ hide some pictures from the treatment group and show all for the control group. Compare the booking rate for the two groups.
    - need to be aware of ethical issues of doing such experiments. If can't run such experiments, find an IV for picutres (what are they? maybe need to talk to the team or the client). I doubt a good natural experiment exists.
#### 11. How would you design an experiment to determine the impact of latency on user engagement?
  - Isolate just that factor using a slowdown experiment, i.e., add a delay in an A/B test.
#### 12. What is maximum likelihood estimation? Could there be any case where it doesn’t exist?
  - A method for parameter estimation (fitting a model). We choose parameters so as to maximize the likelihood of data showing up (assuming the observed outcome would happen most likely given our model).
  - MLE can be seen as a special case of the [maximum a posteriori estimation](https://en.wikipedia.org/wiki/Maximum_a_posteriori_estimation "Maximum a posteriori estimation") (MAP) that assumes a [uniform](https://en.wikipedia.org/wiki/Uniform_distribution_\(continuous\) "Uniform distribution \(continuous\)") [prior distribution](https://en.wikipedia.org/wiki/Prior_probability "Prior probability") of the parameters, or as a variant of the MAP that ignores the prior and which therefore is [unregularized](https://en.wikipedia.org/wiki/Regularization_\(mathematics\) "Regularization \(mathematics\)").
  - it doesn’t exist if you don't have a fully specified parametric model: mm, gmm, semiparametric, nonparametric, etc.
#### 13. What’s the difference between a MAP, MOM, MLE estimator? In which cases would you want to use each?
  - MAP estimates the posterior distribution given the prior distribution and data which maximizes the likelihood function. MLE is a special case of MAP where the prior is uninformative uniform distribution.
  - MOM sets moment values and solves for the parameters. It is a semi-parametric method and has less restrictive assumptions.
#### 14. What is a confidence interval and how do you interpret it?
  - see previous questions
#### 15. What is unbiasedness as a property of an estimator? Is this always a desirable property when performing inference? What about in data analysis or predictive modeling?
  - Unbiasedness means that the expectation of the estimator is equal to the population value we are estimating. 
  - In general, this is desirable because unbiased estimator = we don't make mistakes on average. But it is not always desirable if we face a tradeoff between consistency and unbiasedness. 
    - For example, it is not desirable if the estimator never gets close to the true value.
  - This is not as important in predictive modeling because of the bias variance tradeoff. We sometimes want to prioritize the generalizability and avoid overfitting by reducing variance and increasing bias.
