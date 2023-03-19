# Theory for Bayesian Model

## Assumptions
- Have sufficient data
- Data is clean
- a the expected results of a game is the mean of the previous games
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

After observing a game with result vector $x$ we can update the distribtuion using the game statistics as follows <br>
$$\mu = \mu_{old} + \Sigma_{12}   \sigma_{new}^{-1}    (x - \mu_{old})$$ <br>
$$\Sigma = \Sigma_{old} + \Sigma_{12}   \sigma_{new}^{-1}   \Sigma_{12}^{T}$$

Here we are using the assumption "A the expected results of a game is the mean of the previous games"
We will need to derive vector $\Sigma_{12}$ to define the correlation between previous games

TODO: make block nature of matricies explicit here


