# Text Classification for Turkish News Articles
 Naive Bayes vs Logistic Regression on SUDer data collection with bag-of-words approach.

## Introduction

Deep learning is an extremely popular method today and has had its effect in every field, including text classification. On the other hand, traditional models still offer us an extremely powerful and useful baseline.

In this project, we have trained 2 models that tries to calculate class probabilities with different approaches. Naive Bayes is a generative model which tries to calculate the class probability of agiven instance using the existing distributions of features. This model basically learns the class probabilities by calculating them using Bayes Theorem.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;P(class|data)=\frac{P(data|class)*P(class)}{P(data)}" />

P(data) is evidence which is neglected in calculations.

P(class) is prior and P(class | data) is likelihood.

