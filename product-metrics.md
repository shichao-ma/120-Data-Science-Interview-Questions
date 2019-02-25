## Product Metrics (15 questions)

#### 1. What would be good metrics of success for an advertising-driven consumer product? (Buzzfeed, YouTube, Google Search, etc.) A service-driven consumer product? (Uber, Flickr, Venmo, etc.)
  * display-ads (successful as long as people pay attention, e.g., Coca-Cola): Pageviews and daily actives
  * click-ads (successful when click, e.g., pay-per-click ads): click through rate, cost per click
  * service-driven (successful when purchase): number of purchases, conversion rate
#### 2. What would be good metrics of success for a productivity tool? (Evernote, Asana, Google Docs, etc.) A MOOC? (edX, Coursera, Udacity, etc.)
  * productivity tool: same as premium subscriptions
  * MOOC: same as premium subscriptions, completion rate
#### 3. What would be good metrics of success for an e-commerce product? (Etsy, Groupon, Birchbox, etc.) A subscription product? (Net ix, Birchbox, Hulu, etc.) Premium subscriptions? (OKCupid, LinkedIn, Spotify, etc.) 
  * e-commerce: number of purchases, conversion rate, Hourly, daily, weekly, monthly, quarterly, and annual sales, Cost of goods sold, Inventory levels, Site traffic, Unique visitors versus returning visitors, Customer service phone call count, Average resolution time
  * subscription
    * churn, CoCA, ARPU, MRR, LTV
  * premium subscriptions: conversion rate of premium subs (# of premium subs/ # of total users)

#### 4. What would be good metrics of success for a consumer product that relies heavily on engagement and interaction? (Snapchat, Pinterest, Facebook, etc.) A messaging product? (GroupMe, Hangouts, Snapchat, etc.)
  * heavily on engagement and interaction: uses AU ratios, email summary by type, and push notification summary by type, resurrection ratio
    ** For social network type: network density, interation within/ beyond network, communication health.
  * messaging product: similar to network product. how often do people use it. how much (percantage) communication on this product. How many business owners running on this platform.
#### 5. What would be good metrics of success for a product that offered in-app purchases? (Zynga, Angry Birds, other gaming apps)
  * Depends on the revenue model. If most revenues come from big sharks, then we need to look at retention rate/ spending of sharks. If most revenues come from small purchases, then we can look at 
  ** Average Revenue Per Paid User
  ** Average Revenue Per User
  ** Purchase rate/ count per user in a given time window
#### 6. A certain metric is violating your expectations by going down or up more than you expect. How would you try to identify the cause of the change?
  * breakdown the KPI’s into what consists them and find where the change is
  * then further breakdown that basic KPI by channel, user cluster, etc. and relate them with any campaigns, changes in user behaviors in that segment
  * identify what's changed at the turning point.
#### 7. Growth for total number of tweets sent has been slow this month. What data would you look at to determine the cause of the problem?
  * Is this slow down normal? market saturated? (saturation rate)
  * Look at what's happend outside of twitter this month: new competitors? no major events? holidays? network down in major cities? people moving to mobile in general while current mobile app sucks?
  * Is this caused by a drop in tweets per user or a drop in total active users? (define active user)
  * Is this caused by users in a certain subgroup? (e.g., geographical, demographical)
#### 8. You’re a restaurant and are approached by Groupon to run a deal. What data would you ask from them in order to determine whether or not to do the deal?
  * For similar restaurants (define similarity by customer base, cuisine type, size, business hours, revenue size, etc), average increase in revenue gain per coupon, average increase in customers per coupon. 
  * If my restaurant is not very busy, average increase in table occupation/ turnover rate, average decrease in staff idle time.
  * If my restaurant is new, how many positive reviews on Yelp generated from this campaign?
  * How many customers have joined customer loyalty program (like Starbuck's collecting-star system) if I have one? 
#### 9. You are tasked with improving the efficiency of a subway system. Where would you start?
  * Talk to the client to let them define efficiency and figure out what they are unhappy about.
#### 10. Say you are working on Facebook News Feed. What would be some metrics that you think are important? How would you make the news each person gets more relevant?
  * rate for each action, duration users stay, click through rate for sponsor feed posts, hover duration
  * ref. News Feed Optimization
    * Affinity score: how close the content creator and the users are
    * Weight: weight for the edge type (comment, like, tag, etc.). Emphasis on features the company wants to promote
    * Time decay: the older the less important
#### 11. How would you measure the impact that sponsored stories on Facebook News Feed have on user engagement? How would you determine the optimum balance between sponsored stories and organic content on a user’s News Feed?
  * AB test on different balance ratio and see 
  * Also, figure out a matching algorithm to match customers with relevant sponsored stories using affinity score.
  * Display different number of sponsored stories depending if a customer is using ad-blocker or not.
#### 12. You are on the data science team at Uber and you are asked to start thinking about surge pricing. What would be the objectives of such a product and how would you start looking into this?
  * You don't want such a product to piss people off and leave (or even worse, start another delete Uber campaign).
  ** So you need to be transparant about this program. And give people some discount on non-rush hour.
  * More revenue, either directly or indirectly by increasing market efficiency.
  * Consider a gradual step-function type scaling mechanism until that imbalance of requests-to-drivers is alleviated and vice versa. 
  ** The algorithm should tailored and calibrated to each location as price elasticities almost certainly vary across different cities depending on a huge multitude of variables: income, distance/sprawl, traffic patterns, car ownership, etc. With the massive troves of user data that Uber probably has collected, they most likely have tweaked the algos for each city to adjust for these varying sensitivities to surge pricing. Throw in some machine learning and incredibly rich data and you've got yourself an incredible, constantly-evolving algorithm.  
  * If the above system is too data/ML/resource intensive to implement, then consider a semi-auction system where customers can choose how much money they are going to add on top of the base rate.
  ** Such data can be used to train your model.
  

#### 13. Say that you are Netflix. How would you determine what original series you should invest in and create?
  * Look at which genre is popular.
  * If possible, find some demographics about Netflix's customers and use them to figure out what will they like.
  * Estimate the potential market size for the original series.
#### 14. What kind of services would find churn (metric that tracks how many customers leave the service) helpful? How would you calculate churn?
  * subscription based services, any service that relies on customers continue using the product (ad stream is a major revenue source), services that rely on frequent payments (e.g., games with in-app purchases. even a barber shop). Movie, book, game sequels.
#### 15. Let’s say that you’re are scheduling content for a content provider on television. How would you determine the best times to schedule content?
  * A matching problem. One end is customer type and the other is content type.
