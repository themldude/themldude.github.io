---
layout: post
title: Cross Validation
---

{{ page.title }}
================

<p class="meta">30 Jan 2016</p>

How should you use cross validation to analyze a dataset?

## Analysis without Cross Validation

Consider that you are analysis a regression dataset. So you use the Root Mean Square error (RMSE). We split the dataset into a training set (70%) and test set (30%).

An analysis for a Machine Learning algorithm includes these experiments:

- Model Complexity Experiments
- Learning Curve Experiments

What is the purpose of these?

In the Model Complexity Experiments you change the model by varying the hyperparameters of the model. You record RMSE errors in each case. (The k in kNN is a hyperparameter, the number of hidden nodes/layers, momentum and learning rates in a Neural Network are hyperparameters.)

The hyperparameters that gives you the lowest error on the '''test set''' are your optimal hyperparameters. This gives you the "best" model. By best, we mean it is the model that best generalizes: it is the model with the least bias and least variance.

The Learning Curve Experiments help you to determine how much data you need to learn this "best" model. It gives you a lower bound on the samples needed to learn this model. Isn't this useful? If you are trying to buy a house in Atlanta, you want to know what is the minimum number of houses you want to explore before you understand the housing market here and put your bid.

The Learning Curve experiments also gives you a second check to prove that the model you selected actually does not have high bias or high variance. [To understand this, watch this video](https://www.youtube.com/watch?v=g4XluwGYPaA).

## Cross Validation

Ok, so now where does cross validation play into this? Let's watch this video.

Cross validation is simply a new way to find the hyperparameters for the "best" model. But why use cross validation? To remove bias due to your data.

Lets say that you have a dataset of all houses in Buckhead, Marietta, Decatur and Downtown (suburbs) in Atlanta. And you are trying to find a model that can estimate the cost of any house in Atlanta. You don't want to train your data on the houses of Buckhead and Marietta alone. So perhaps you randomly reshuffle your data and partition them into folds. If you have 10 folds, you train on 9 folds and find the error for the 10th fold. If you repeat this procedure for all the 10 folds, you can find an average error. This error is a better estimate of the training error (also called cross validation error now because, duh, you used cross validation). Run the model on your test set to get the test error.

## Conclusion

In conclusion, cross validation is just a fancy new way to do training.

How to split the data into 70/30?

If you consider the housing example again, you don't want your test set (30%) to be biased (For example, most of the samples are houses in Downtown). So somehow you need to make sure that the training data and testing data equally represent houses in all the four suburbs. How do you that? Random sampling, or more accurately Stratified Sampling.

You can do some analysis to determine if you did the 70/30 split properly, but thats beyond the course for now. But a simple way to do it is to draw histograms of your training and testing data. The histograms will show how many houses from each suburb are in these data sets. If the histograms look similar, you did the split properly. Comparing histograms is not beyond this course, do that.