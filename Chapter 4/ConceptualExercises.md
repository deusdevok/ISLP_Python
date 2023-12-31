# Chapter 4 Conceptual Exercises

1. The logistic function is:

    $$p(X) = \frac{e^{\beta_0+\beta_1 X}}{1+e^{\beta_0+\beta_1 X}}$$

    $$p(X) (1+e^{\beta_0+\beta_1 X}) = e^{\beta_0+\beta_1 X}$$

    $$p(X) = (1-p(X))e^{\beta_0+\beta_1 X}$$

    $$\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1 X}$$

    The expression $p(X)/(1-p(X))$ is called *odds*.

    Taking the natural logarithm, we arrive at the *logit* or *log odds* function:

    $$\boxed{\log\left(\frac{p(X)}{1-p(X)}\right) = \beta_0+\beta_1 X}$$

2. We want to classify an observation into one of *K* classes. Let $\pi_k$ be the prior probability that a randomly chosen observation belongs to the *kth* class. Let $f_k(X)=P(X|Y=k)$ be the *density function* of X coming from the *kth* class.

    Bayes theorem:

    $$P(Y=k|X=x) = p_k(x) = \frac{P(Y=k \bigcap X=x)}{P(X=x)}$$

    $$p_k(x) = \frac{P(X=x|Y=k) P(Y=k)}{P(X=x)}$$

    $$p_k(x) = \frac{P(Y=k) P(X=x|Y=k)}{\sum_{l=1}^K P(X=x|Y=l) P(Y=l)}$$

    $$p_k(x) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)}$$

    For the Linear Discriminant Analysis (LDA) with one predictor ($p=1$), we assume $f_k(x)$ to be Gaussian (normal). We also assume that all classes share the same variance, called $\sigma^2$. Then:

    $$p_k(x) = \frac{\pi_k \frac{1}{\sqrt{2\pi} \sigma}e^{-\frac{1}{2\sigma^2}(x-\mu_k)^2}}{\sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi} \sigma}e^{-\frac{1}{2\sigma^2}(x-\mu_l)^2}}$$

    Bayes classifier involves assigning an observation $X=x$ to the class $k$ for which $p_k(x)$ is largest. Taking the natural logarithm:

    $$\log(p_k(x)) = \log(\pi_k) - \log(\sqrt{2\pi}\sigma) - \frac{(x-\mu_k)^2}{2\sigma^2} - \log\left(\sum_{l=1}^K [\cdots]\right)$$

    The second and last term of the previous expression are *independent* (constant) with respect to *k*, which means that those terms won't affect the maximization and can be dropped.

    $$\log(p_k(x)) \sim \log(\pi_k) - \frac{x^2}{2\sigma^2} + \frac{2x\mu_k}{2\sigma^2} - \frac{\mu_k^2}{2\sigma^2}$$

    Again, the second term is independent of *k*, and it can be dropped. We can use the following expression to maximize, in order to assign an observation to the class for which the expression is largest.

    $$\boxed{\delta_k(x) = x\frac{\mu_k}{\sigma^2} - \frac{\mu_k^2}{2\sigma^2} + \log(\pi_k)}$$

    This expression is linear in *x*, hence the name *Linear* Discriminant Analysis. The *discriminant* refers to the $\delta_k(x)$ function to be maximized.

3. Quadratic Discriminant Analysis. Now we assume $X \sim N(\mu_k, \sigma_k^2)$:

    $$f_k(x) = \frac{1}{\sqrt{2\pi} \sigma_k}e^{-\frac{1}{2\sigma_k^2}(x-\mu_k)^2}$$

    Now we want to maximize:

    $$p_k(x) = \frac{\pi_k \frac{1}{\sqrt{2\pi} \sigma_k}e^{-\frac{1}{2\sigma_k^2}(x-\mu_k)^2}}{\sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi} \sigma_l}e^{-\frac{1}{2\sigma_l^2}(x-\mu_l)^2}}$$

    The $\sqrt{2\pi}$ can be cancelled out:

    $$p_k(x) = \frac{\pi_k \frac{1}{\sigma_k}e^{-\frac{1}{2\sigma_k^2}(x-\mu_k)^2}}{\sum_{l=1}^K \pi_l \frac{1}{\sigma_l}e^{-\frac{1}{2\sigma_l^2}(x-\mu_l)^2}}$$

    Taking logarithms:

    $$\log(p_k(x)) = \log(\pi_k) - \log(\sigma_k) - \frac{(x-\mu_k)^2}{2\sigma_k^2} - \log\left(\sum_{l=1}^K [\cdots]\right)$$

    The last term is independent of *k*, so the discriminant becomes:

    $$\boxed{\delta_k(x) = - \frac{(x-\mu_k)^2}{2\sigma_k^2} + \log(\pi_k) - \log(\sigma_k)}$$

    For this case, the discriminant becomes quadratic in *x*.

4. KNN Curse of Dimensionality.
  a) $(0.65-0.55)/1 = 0.10$ which corresponds to the $10\%$ of the data.
  b) $(0.65-0.55)\cdot (0.4-0.3)\cdot 1 = 0.01$ which corresponds to the $1\%$ of the data.
  c) $0.1^{100} = \frac{1}{10^{100}}$ is the fraction of the available observations used to make a prediction.
  d) When the number of features increases, this methods makes the available observations near a given test observations decreases exponentially. In the limit, it tends to zero: $\lim_{p\to \infty} 0.1^p = 0$.
  e) What is the length of each side of the hypercube in *p* dimensions so that the volume is the 10% of the hypercube of length 1? $a^p = 0.1$, then $a = 0.1^{1/p}$.

5. Differences between LDA and QDA.
  a) On the training set, QDA would perform better than LDA (possibly overfitting). On the test set, LDA performs better, since the Bayes decision boundary is linear.
  b) If the Bayes decision boundary is non-linear, then QDA would perform better than LDA, both on the training and test sets. This is assuming the non-linearity is close to quadratic. In other cases, QDA may perform poorly than LDA.
  c) If the sample size *n* is very large, one would expect QDA to perform better than LDA.
  d) **False**. What we can achieve by using QDA on a linear Bayes decision boundary is an increase in performance in the *training* set. But in the *test* set it would probably perform worse, because of overfitting.

6. The logistic regression model is:
  $$p(X) = \frac{e^{\beta_0 + \beta_1 X_1 + \beta_2 X_2}}{1 + e^{\beta_0 + \beta_1 X_1 + \beta_2 X_2}}$$

  a) Plugging the values:

  $$p(X) = \frac{e^{-6 + 0.05\cdot 40 + 1\cdot 3.5}}{1 + e^{-6 + 0.05\cdot 40 + 1\cdot 3.5}} = 0.3775 = 37.8\%$$

  b) Solve for $X_1$:

  $$p(X) = \frac{e^{-6 + 0.05\cdot X_1 + 1\cdot 3.5}}{1 + e^{-6 + 0.05\cdot X_1 + 1\cdot 3.5}} = 0.5$$

  $$\frac{e^{-2.5 + 0.05\cdot X_1}}{1 + e^{-2.5 + 0.05\cdot X_1}} = 0.5$$

  $$e^{-2.5 + 0.05\cdot X_1} = 0.5\cdot (1 + e^{-2.5 + 0.05\cdot X_1})$$

  $$0.5\cdot e^{-2.5 + 0.05\cdot X_1} = 0.5$$

  $$e^{-2.5 + 0.05\cdot X_1} = 1$$

  Applying logarithm to both sides:

  $$-2.5 + 0.05\cdot X_1 = 0$$

  $$X_1 = 50$$

7. Using Bayes theorem

  $$P(Y=yes|X) = \frac{P(X|Y=yes)\cdot P(Y=yes)}{P(X)}$$

  $$P(Y=yes|X) = \frac{P(X|Y=yes)\cdot P(Y=yes)}{\sum_{k=(yes,no)} P(X|Y=k)\cdot P(Y=k)}$$

  $$P(Y=yes|X) = \frac{f_{k=yes}(x)\cdot P(Y=yes)}{\sum_k f_k(x)\cdot P(Y=k)}$$

  $$P(Y=yes|X) = \frac{0.8\cdot\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-10)^2/2\sigma^2}}{0.8\cdot\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-10)^2/2\sigma^2} + 0.2\cdot\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-0)^2/2\sigma^2}}$$

  After some algebra:

  $$P(Y=yes|X) = \frac{1}{1 + 0.25\cdot e^{[-x^2+(x-10)^2]/2\sigma^2}}$$

  Using $x=4$ and $\sigma^2=36$:

  $$\boxed{P(Y=yes|X=4) = 0.752}$$

8. In the case of 1-NN (KNN with K=1), the training error is 0%. This is because when the algorithm looks for the one training data point that is closest to itself, it will find the same point. Therefore, the overall error in the train set is equal to 0 (perfect fit). If the average between the train and test error rates is 18%, then the test error rate is 36% (double). The 1-NN algorithm is clearly overfitting the data. Then, we should prefer logistic regression because the test error rate is 30%, which is lower than 36%.

9. The expression for the odds is:
  $$odds = \frac{p}{1-p}$$

  a) Compute probability given odds:

  $$0.37 = \frac{p}{1-p}$$

  $$0.37\cdot(1-p) = p$$

  $$0.37 = 1.37\cdot p$$

  $$\boxed{p = 0.27 = 27\%}$$

  b) Compute odds given probability:

  $$odds = \frac{0.16}{1-0.16}$$

  $$\boxed{odds = 0.19 = 19\%}$$

12. Odds. Log odds is also called *logit*.
  a) $$odds = \frac{p}{1-p} = \frac{\frac{e^{\beta_0+\beta_1 x}}{1+e^{\beta_0+\beta_1 x}}}{1-\frac{e^{\beta_0+\beta_1 x}}{1+e^{\beta_0+\beta_1 x}}}$$

  $$odds = \frac{\frac{e^{\beta_0+\beta_1 x}}{1+e^{\beta_0+\beta_1 x}}}{\frac{1+e^{\beta_0+\beta_1 x}-e^{\beta_0+\beta_1 x}}{1+e^{\beta_0+\beta_1 x}}} = e^{\beta_0+\beta_1 x}$$

  $$\boxed{\log(odds) = \beta_0+\beta_1 x}$$

  b) $$odds = \frac{p}{1-p} = \frac{\frac{\exp(\alpha_{orange_0} + \alpha_{orange_1}x)}{\exp(\alpha_{orange_0} + \alpha_{orange_1}x) + \exp(\alpha_{apple_0} + \alpha_{apple_1}x)}}{1-\frac{\exp(\alpha_{orange_0} + \alpha_{orange_1}x)}{\exp(\alpha_{orange_0} + \alpha_{orange_1}x) + \exp(\alpha_{apple_0} + \alpha_{apple_1}x)}}$$

  $$odds = \frac{\frac{\exp(\alpha_{orange_0} + \alpha_{orange_1}x)}{\exp(\alpha_{orange_0} + \alpha_{orange_1}x) + \exp(\alpha_{apple_0} + \alpha_{apple_1}x)}}{\frac{\exp(\alpha_{orange_0} + \alpha_{orange_1}x) + \exp(\alpha_{apple_0} + \alpha_{apple_1}x) - \exp(\alpha_{orange_0} + \alpha_{orange_1}x)}{\exp(\alpha_{orange_0} + \alpha_{orange_1}x) + \exp(\alpha_{apple_0} + \alpha_{apple_1}x)}}$$

  $$odds = \frac{\exp(\alpha_{orange_0} + \alpha_{orange_1}x)}{\exp(\alpha_{apple_0} + \alpha_{apple_1}x)}$$

  $$\boxed{\log(odds) = (\alpha_{orange_0}-\alpha_{apple_0}) + (\alpha_{orange_1}-\alpha_{apple_1})\cdot x}$$

  c) Assuming log odds of both models to be the same, then:

  $$\beta_0 = \alpha_{orange_0} - \alpha_{apple_0}$$

  $$\beta_1 = \alpha_{orange_1} - \alpha_{apple_1}$$

  Here, we can set $\alpha_{apple_0} = 0$ and $\alpha_{apple_1} = 0$. Then:

  $$\beta_0 = \alpha_{orange_0} = 2$$

  $$\beta_1 = \alpha_{orange_1} = -1$$

  d) In this case (*On page 196, exercise 12d, the last two estimates should have the subscript “apple” instead of “orange”. Thanks to Sundong Kim.*, [errata link](https://www.statlearning.com/errata-python-edition)):

  $$\beta_0 = 1.2 - 3 = -1.8$$

  $$\beta_1 = -2 - 0.6 = -2.6$$

  e) I don't know how the 2000 test observations fits into the data in this exercise.