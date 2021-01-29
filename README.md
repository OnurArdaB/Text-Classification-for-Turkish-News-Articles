# Text Classification for Turkish News Articles

 Naïve Bayes vs Logistic Regression on SUDer data collection with bag-of-words approach.

## Introduction

Today, text classification is one of the popular approaches to natural language processing. Although deep learning methods offer extremely high performance against these problems, similar results can be obtained with traditional approaches. For this reason, we trained Naïve Bayesian and Logistic Regression in this project to see the performance differences of Productive and Discriminatory Models. This comparison was initially made because both of these models were trying to calculate the same probabilities. In this process, the approaches of the models on probability calculations cause obvious effects on their performance. The aforementioned approaches are discussed in more detail in the following sections.

## Generative Model: Naïve Bayes

Naïve Bayes is a supervised machine learning algorithm which uses Bayes Theorem in order to calculate the most likely class (maximum posterior probability) of a given data instance.

Basically we are trying to calculate the class *c* which has the maximum posterior probability using the following equation.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;Class=argmax(P(c|d))" />

Let's recall Bayes Rule 

<img src="https://latex.codecogs.com/svg.latex?\Large&space;P(a|b)=\frac{{P(b|a)}\times{P(a)}}{P(b)}" />

Modifying a little bit for better interpretation

<img src="https://latex.codecogs.com/svg.latex?\Large&space;P(class|data)=\frac{{P(data|class)}\times{P(class)}}{P(data)}" />

Apply the Bayes Rule in order to solve our initial equation

<img src="https://latex.codecogs.com/svg.latex?\Large&space;Class=argmax(\frac{{P(data|class)}\times{P(class)}}{P(data)})" />

Denominator is dropped which is not important

​																				*likelihood*                        	*prior*

<img src="https://latex.codecogs.com/svg.latex?\Large&space;Class=argmax({P(data|class)}\times{P(class)})" />



There are lots of other details that can be discussed for Naïve Bayes Classifier but the main important field that we should discuss is that how it estimates the probability of every possible combination of features observed.

It would not be a false statement to make that each feature combination would require a very large set of parameters.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;Class=argmax({P(f1,f2,...fN|class)}\times{P(class)})" />



This condition forces us to make a simplifying assumption which is the Conditional Independence Assumption

 - This is why its called Naïve Bayes since it assumes that each input variable is entirely independent of each other.

 - What this means is that we are basically assuming features such as 'çok' and 'güzel' are independent of each other.

 - As a result of this assumption
    - <img src="https://latex.codecogs.com/svg.latex?\Large&space;{P(f1,f2,...fN|class)}={P(f1|class)}{P(f2|class)}...{P(fN|class)}" />
    - It is not guaranteed to have these assumptions hold all the time but such assumption makes our problem much simpler than it was initially.

There also exists some other issues such as log taking in maximum likelihood estimation and Laplace Smoothing which can be read in here.

Finally, we are using our training data in bag-of-words format (basically using term frequencies of words neglecting the word order)

### Summary of Naïve Bayes

 - Results are very high despite the fact that we are using a much simpler approach than other methods.
 - Much more faster to train
 - Less likely to overfit
 - Even though the resulting probabilities are not very accurate model still manages to make right classifications.



## Discriminative Model: Logistic Regression

Logistic Regression is also a supervised machine learning algorithm for classification problems that tries to calculate the maximum posterior probability in such a manner that directly learns from the dataset without trying to generate probabilities by observing smaller set of probabilities inside the dataset.

It tries to extract weights from the input, combining them linearly with taking their logs. Each feature is multiplied by a weight and then summed.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;Class=argmax(P(c|d))" />

<img src="https://latex.codecogs.com/svg.latex?\Large&space;P(class|data)=$$\sum_{i=1}^Nw_if_i  " />

Initially, we come across a problem in above equation since we are getting values from -inf to inf which are not acceptable probabilities. We solve this problem by modifying the right hand side such that it maps the results in a space of results ranging from 0-to-1.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;  
\sigma( w^T x + b) = \frac{1}{1 + e^{-(w^T x + b)}}
\text  Sigmoid" />

<img src="https://latex.codecogs.com/svg.latex?\Large&space;P(class|data)=\dfrac{exp(\sum_{i=1}^Nw_if_i)}{\sum_{C}exp(\sum_{i=1}^Nw_if_i)}" />

![How do Conditional Random Fields (CRF) compare to Maximum Entropy Models  and Hidden Markov Models? - Quo… | Logistic regression, Machine learning  models, Regression](https://i.pinimg.com/originals/1d/3f/9c/1d3f9cefc0de33cfebe71bbc237ccc6b.png)



Logistic Regression out-performs the Naïve Bayes most of the time since in text classification, statistically independent features are not very likely to occur compared to dependent ones.

​						çok güzel is a sample where they are very likely to be dependent.

### Summary of Logistic Regression

 - Naïve Bayes might fail to calculate proper results if its Naïve Assumption does not hold since;
    - Any two feature that are actually correlated would be accepted as not correlated causing the multiplication of probabilities of features to overestimate.
    - Hence, Logistic Regression is much more robust to correlated features.

