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
  e) What is the length of each side of the hypercube in *p* dimensions so that the volume is the 10% of the hypercube of length 1? $a^p = 0.1$, then $a = 0.1^{1/p}$