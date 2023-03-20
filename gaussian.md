# Theory for Bayesian Model

## Assumptions
- 1. Have sufficient data
- 2. Data is clean
- 3. 
- 4. The probability distribtion predicitng the statistics does not change significantly between games.
- 5. Data follows a joint gaussian distribution
- 6. A teams performance has a high correlation between games that are close together in time and low correlation between games that are far apart in time

## Theory
First take a set of previous games of a team, for example the previous season. Each game will generate a 'results vector' containing the statistics of the game. Plotting this in high-dimentional space, a cloud will form (assumptions 1,2,5).  

We can fit this data with a gaussian distribtion, see resources:

https://fabiandablander.com/r/Curve-Fitting-Gaussian.html <br>
https://www.mathworks.com/help/curvefit/gaussian.html

The result of this analysis will result in an average results vector $\mu_{prev}$ (length n) and a covariance matrix $\Sigma_{prev}$ (n by n). We can use this distribution to predict the performance of a team.

Once the first new game happens, a new results vector will be generated $\mu_{new}$. Using assumption 4, we know this measurement was made with certainty described by $\Sigma_{new} = \Sigma_{prev}$ * c$ where $c$ is a hyperparameter. Via assumption 6, the correlation between these two distributions is given by $\Sigma_{joint} = \Sigma_{prev} \exp{(-\frac{||a, b||^2}{2 \sigma^2})}. Here let $a=0$ and $b=1$ and $\sigma$ is a hyperparameter.

We can now define a conditional distribtuion to predict the next game:

$$\mu_{next} = \mu_{old} + \Sigma_{joint}   \sigma_{old}^{-1}    (\mu_{new} - \mu_{old})$$ <br>
$$\Sigma_{next} = \Sigma_{new} + \Sigma_{joint}   \sigma_{old}^{-1}   \Sigma_{joint}^{T}$$

In reality the distribution defined by $\mu_{next} \Sigma_{next}$ is a refined distribution to predict the output of the game that just happened.

https://en.wikipedia.org/wiki/Multivariate_normal_distribution#Conditional_distributions

Flaws:
  - Doesn't consider opponent when creating $\mu_{new}$ or $\Sigma_{new}$


