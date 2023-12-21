# Chapter 3 Conceptual Exercises

1. The null hypotheses to which the p-values given in Table 3.4 correspond. The table shows least squares coefficient estimates of the multiple linear regression of number of units sold on TV, radio and newspaper advertising budget. This corresponds to the Advertising dataset.
   The p-value for each predictor (TV, radio, newspaper) correspond to the null hypotheses $H_0$: *"There is **no** relashionship between the predictor (TV, radio or newspaper) and the amount of sales, while keeping the other predictors fixed"*.
   Mathematically, for a model like $sales=\beta_0+\beta_1\times TV+\beta_2\times radio + \beta_3\times newspaper$, the null hypotheses for the TV p-value would be $\beta_1 = 0$.
   By looking at the p-values in the table, one can conclude that TV and radio have p-values significantly low, meaning the null hypotheses can be rejected in favour of the alternative hypotheses, which means there is a relation between sales and TV and radio budgets.
   On the other hand, the p-value associated with newspaper is significantly high, meaning that there is no clear relashionship between newspaper budget and sales.

2. Differences between KNN classifier and regression:
   **KNN classifier**: This methods makes predictions in a classification scenario. Given a value of $K$ and a point $x_0$, take the $K$ points that are closer to $x_0$ and compute the probabilities for each class. The class with higher probability will be the predicted class for $x_0$.
   **KNN regression**: As opposed to KNN classifier, KNN regression is used for regression problems. Given a value of $K$ and a point $x_0$, it looks for the $K$ closest points to $x_0$ in the training data, and then estimates $f(x_0)$ by computing the average of those $K$ values.
   **Difference between KNN classifier and regression**. The main difference is that one is used for classification, and the other for regression problems. The way to make predictions is similar in the way that the method looks for the $K$ closest points to $x_0$. But the difference is that for classification is uses the most probable point to classify the data, while for regression it uses all the $K$ points to compute an average value for the predicted function value at that point.

3. Data set with five predictors:
   * $X_1 =$ GPA (Grade Point Average)
   * $X_2 =$ IQ (Intelligence Quotient)
   * $X_3 =$ Level (1: College; 0: High School)
   * $X_4 =$ Interaction between GPA and IQ.
   * $X_5 =$ Interaction between GPA and Level.
   * Response: Starting salary after graduation (in $1000's of dollars).

   After using least squares to fit the model we obtain:
   * $\hat{\beta_0} = 50$
   * $\hat{\beta_1} = 20$
   * $\hat{\beta_2} = 0.07$
   * $\hat{\beta_3} = 35$
   * $\hat{\beta_4} = 0.01$
   * $\hat{\beta_5} = -10$

   a) True or False
      * i) **False**. Fixing IQ and GPA, since $X_3$ is either 0 or 1, and the corresponding parameter is $\hat{\beta_3} = 35$ (which is greater than 0), using a value of 1 for $X_3$ increases the response (salary). Then, College graduates earn more (on average) than High School graduates.
      * ii) **True**. The explanation is the same as point **i)**.
      * iii) **True**. The interaction term $X_5$ between GPA and Level is present only when Level is equal to 1 (College students). The corresponding parameter is $\hat{\beta_5} = -10$. Since this parameter is negative, the response decreases as this term increases in absolute value. Let's assume GPA has the maximum value of 4.0. For High School, Level is 0, then the response is:
      $$S_{highschool} = 50+20\times 4.0+0.07\times IQ+0.01\times 4.0\times IQ = 130 + 0.11\times IQ$$
      While for College is:
      $$S_{college} = 50+20\times 4.0+0.07\times IQ+35+0.01\times 4.0\times IQ-10\times 4.0 = 125 + 0.11\times IQ$$
      Then, if GPA is high enough, High School graduates can earn more than college graduates.
      * iv) **False**. If GPA is high enough, as seen in **iii)** College graduates don't earn more than High school graduates.

   b) For a College graduate with IQ of 110 and GPA of 4.0, the prediction is:
   $$S = 50 + 20\times 4.0 + 0.07\times 110 + 35\times 1 + 0.01\times 4.0\times 110 - 10\times 4.0\times 1$$

   $$S = 137.1 \text{ (thousands USD)}$$

   c) **False**. The value can be significant depending on the values of GPA and IQ. One measure that can tell weather the interaction is significant or not is the p-value, not the coefficient.

4. Fitting two models: linear and cubic.
   a) For the training data, adding more parameters to the model will always decrease the RSS. This is called *overfitting* the model.
   b) For the test data, on the other hand, it is highly possible that the RSS will increase for the cubic model. Because we know that the true relashionship is in fact linear, adding more variables to the model will not fit the test data well, and thus increase the RSS.
   c) If we know that the true relashionship is not linear, then the RSS for the cubic model in the training data should be lower than for the linear model. Adding more parameters to the model should fit the data better. (This is the same as **a**: The RSS for the training data always decrease when adding more parameters to the model).
   d) For the test data, RSS should also be smaller for the cubic model. This is because the true relashionship is not linear, and then adding more parameters to the model will fit the test data better.

5. Linear regression without intercept.

   $$\hat{y_i} = x_i \hat{\beta}$$

   If $\bar{x}=\bar{y}=0$, then we can write:

   $$\beta = \frac{\sum_i x_i y_i}{\sum_j x_j^2}$$

   Then:

   $$y_i = x_i \frac{\sum_j x_j y_j}{\sum_k x_k^2}$$

   $$y_i = \sum_j \frac{x_i x_j}{\sum_k x_k^2}y_j$$

   $$y_i = \sum_j a_{j(i)} y_j$$

   Then, we can see that $a_j$ (with a subindex $i$) is:

   $$a_{j(i)} = \frac{x_i x_j}{\sum_k x_k^2}$$

6. Using the coefficients from the least squares:

   $$y = \beta_0 + \beta_1 x$$

   $$y(\bar{x}) = \beta_0 + \beta_1 \bar{x}$$

   Since $\beta_0 = \bar{y} - \beta_1\bar{x}$,

   $$y(\bar{x}) = (\bar{y} - \beta_1 \bar{x}) + \beta_1 \bar{x}$$

   $$y(\bar{x}) = \bar{y}$$

   Then, the least squares line passes through $(\bar{x}, \bar{y}).$