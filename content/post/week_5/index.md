---
title: Week 5
date: '2024-10-07'
categories:
  - blog-posts
tags:
  - Week5
---

Week 5: Demographics and Comprehensive Modeling

This week, we examined the effects of demographic values on voter turnout and vote choice, based on a paper by Kim and Zilinsky (2023).

The demographics we looked at are age, gender, race, income, and education. Although there are certainly some correlations between demographics and those who vote (active voters are more often older, white, & educated), the study concludes that demographics alone do not tell us that much about partisanship and vote choice. Specifically, a model trained on demographics alone has about a 60% accuracy rate, which holds during our replication of the analysis. This does not significantly improve on a coin flip between the two parties, suggesting that demographics are not a very strong predictor. It was also found that the amount of overall turnout does not push elections in one particular direction.

Therefore, demographics and turnout do not appear to statistically significantly affect the results of an election, despite popular belief.

For experiment's sake, I still tried to make an Electoral College prediction using a combination of demographics and state polling. However, not every state had polling data available to use, so of the 19 states that had polling data, the model predicts 198 votes for Democrats and 101 for Republicans. I then tried to create an electoral prediction that is proportionate to this for all states, with the full knowledge that this could subject itself to confounders (who's more likely to have poll data?), but just to see how effective the subset was at predicting the rest of the electoral votes. It ended up with 356 electoral votes for Democrats to 181 for Republicans, which seemed like a very skewed estimate compared to most other estimates. I think this makes sense because larger states with more urban areas might be more likely to have poll data and also might be more likely to skew Democratic. Although it was interesting to see, I wasn't sure I should use any of this in the combined predictive model.

When I developed my first combined predictive model, I decided to leave out demographics from the equation, since it was the only variable we've looked at so far that proved somewhat statistically insignificant. Instead, I have ensembled previous popular vote, economics, polling, and incumbency into an elastic-net multivariate regressor in order to get a popular vote number. I did so by working from the model ensembling work we did in week 4 but removing the incumbency filter and adding variables as needed. The elastic-net regressor incorporates sparsity and focuses in on the most pertinent features, which is a benefit in our situation because we are analyzing so many dimensions/variables. 

In order to get an electoral vote number, I tried to modify the code to train on the electoral college variable as the y-value instead of the popular vote. However, I wasn't yet able to find the right data that I needed in order to actually replicate this analysis on a national level. When we have analyzed electoral votes in the past, it has been by finding popular vote averages for individual states and grouping them together, weighting them by their electoral vote numbers. However, all the data I've used about the economy, demographics, etc. doesn't necessarily break up easily by state, so it wouldn't really make sense to reuse that method, nor is it possible with the current data to simply swap in the electoral vote number for the popular vote number.

This means that my popular vote and electoral predictions for this week differ vastly because they were created with two very different methods. However, I am putting much more faith in my popular vote prediction because of the problems with the electoral prediction discussed above. 

In the future, I will try to compile full electoral vote numbers from each election year into another dataset and use that to apply similar nationwide methods to get electoral vote estimates using similar types of regression on my national variables. 
