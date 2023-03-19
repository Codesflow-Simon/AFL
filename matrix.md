# Theory for Bayesian Model

## Assumptions
- Have sufficient data
- Data is clean
- Data follows a joint gaussian distribution

## Theory
Consider a cloud of points in high dimentional space, where each axis is a feature for a given team. 

Perhaps we can add estimated win chance to this?

We can fit this data with a gaussian distribtion, see resources:

https://fabiandablander.com/r/Curve-Fitting-Gaussian.html <br>
https://www.mathworks.com/help/curvefit/gaussian.html

This allows us to estimate a teams stats before the game has happened.

Once a game has happened, we can improve our model using Bayes theorem and conditonal distrubtions
https://en.wikipedia.org/wiki/Multivariate_normal_distribution#Conditional_distributions

Written formally:
Take a prior set of data $X$. We can fit a Gaussian $D$ to this data.
$$D = N(\mu, \Sigma) $$ where $\mu$ is a vector length $n$ and $\Sigma$ is a $n$ by $n$ matrix.


