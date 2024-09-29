---
title: Week 3
date: '2024-09-23'
categories:
  - blog-posts
tags:
  - Week3
---

So far, we’ve been looking at predictions using data about previous elections, relative to basic
factors (incumbency, party) as well as to measures of economic well-being. However, we have a
much more recent dataset into which we have not yet tapped: the thousands of public opinion
polls that are conducted each year. Through the principles of sampling, polls appear to be
relatively good estimates; a random subset of the population will behave, on average, similarly
to the whole population. But this doesn’t mean polls have always gotten it right in practice; one
of the most significant examples of this was 2016, where by and large, the polls famously
predicted the wrong winner.
This leads us to explore the week’s guiding question: How can we best use polls to predict
election outcomes?
To understand the polls’ behavior so far in the 2024 cycle, I visualized the variation over time
and against key events:
First, I added key events in 2024 to help understand the poll variation we’ve seen so far this
year. In context of the timings, the major jump in Democratic approval in this graph is explained
by Biden’s exit from the race on July 21st and subsequent handoff to Vice President Harris.
Both parties’ approval rates have most recently been increasing, which could potentially be
related to the recent dropout of independent candidate Robert F. Kennedy Jr. and the influx of
third-party voters resigning themselves to approving of one of the two major parties.
Next, I used some of the machine learning methods we went over in lab to create predictions
based on the polls. We had learned how to create predictions based on the national polls, using
the regularized elasticnet regression method, which resulted in a prediction of 51.79268% for
Harris and 50.65879% for Trump.
To build on this initial foundation, I tried looking at state polls. For the state I had chosen to
analyze, Pennsylvania, I found that the state poll data only had one or two polls for each
election year. This was not enough data to constitute a good training set, so I considered my
other options. One would be using all the state data in aggregate and indiscriminately, but I
didn’t think that would produce a very meaningful estimate, as which state a poll came from
would have no effect on how it was weighted. Another option would be to collect more data on
state-specific polls, which could be a good approach in the future.
I then shifted my focus to creating a model based on the assessments of poll quality and their
resulting performance in 2020, so that I could assign a predicted error to each poll based on
correlations with its FiveThirtyEight graded score and potentially other poll quality factors. I
created an ordinary least squares model to achieve this for 2020. I converted the letter grades
to a numeric scale, so that I could perform a linear regression on the poll grades. This found a
correlation between poll grades and error, as visualized below (1 = best; 10 = worst), but FTE
has since changed its grading system from a letter grade to a different numeric scale; therefore,
I couldn't reapply this model to 2024 data accurately.
If I could establish a direct conversion rate between the old and new FTE scales, I would be
able to use this scale to convert the 2020 correlation data to a 2024 prediction data.
In the future, I would see if I could find the conversion scale so that I could actually use this to
create an updated 2024 prediction model!