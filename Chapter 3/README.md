# Chapter 3 Summary

## Abbreviations

RSS: Residual Sum of Squares

## Minimizing RSS

Using the definition of Residual Sum of Squares:

$$RSS = \sum(y_i-\beta_0-\beta_1x_1)^2$$

Taking the derivative with respect to $\beta_0$:

$$\frac{\partial}{\partial \beta_0}RSS = -2\sum(y_i-\beta_0-\beta_1x_1) = 0$$

$$\sum y_i - n\beta_0 - \beta_1\sum x_i = 0$$

$$\beta_0 = \frac{\sum y_i}{n} - \beta_1\frac{\sum x_i}{n}$$

$$\boxed{\beta_0 = \bar{y} - \beta_1\bar{x}}$$

Replacing this result in the derivative with respect to $\beta_0$:

$$RSS = \sum[y_i-(\bar{y}-\beta_1\bar{x})-\beta_1x_i]^2$$

$$RSS = \sum[(y_i-\bar{y})-\beta_1(x_i-\bar{x})]^2$$

Taking the derivative with respect to $\beta_1$:

$$
\frac{\partial}{\partial \beta_1}RSS = -2\sum\left[(y_i-\bar{y})-\beta_1(x_i-\bar{x})\right]\left(x_i-\bar{x}\right) = 0
$$


$$\sum(y_i-\bar{y})(x_i-\bar{x}) - \beta_1\sum(x_i-\bar{x})^2 = 0$$

$$\boxed{\beta_1 = \frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2}}$$