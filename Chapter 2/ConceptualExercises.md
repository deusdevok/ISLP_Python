# Chapter 2 Conceptual Exercises

1. The performance of a statistical learning method depends on the fact of being flexible or not.
   **a)** Sample size `n` is large, while number of predictors (features) `p` is small. In this case the performance of a flexible statistical learning method is expected to be better than an inflexible one.

   **b)** Number of predictors `p` is large, number of observations `n` is small. In this case an inflexible method could work better.

   **c)** If the relation between the predictors and the response is known to be highly non-linear, then a flexible method should be used. The reason is because an inflexible method can adapt better to the non-linearities of the relation.

   **d)** When the variance of the error terms $\sigma^2=Var(\epsilon)$ is extremely high, this could indicate that the data contains too much noise. Then, a flexible method could try to pick up those noises but won't be better at generalizing. An inflexible method should work better for predicting new observations.

2. Classification or Regression? Inference or Prediction? Provide `n` and `p`
   **a)** Regression (CEO salary is a continuous variable). Inference, because the goal is to understand which factors affect salary instead of making predictions. `n=500`, `p=3` (profit, number of employees and industry).

   **b)** Classification (success or failure). Prediction. `n=20`, `p=13` (price charged, marketing budget, competition price and ten other variables).

   **c)** Regression (a percent change is a floating variable). Prediction. `n=4*12=48`, `p=3` (US, British, German %).

3. Bias-variance decomposition
   **a)** Sketch of bias (squared), variance, training error, test error and bayes curves.

   ![curves](https://raw.githubusercontent.com/deusdevok/ISLP_Python/main/Chapter%202/ex3curves.png "Sketch curves")
   https://raw.githubusercontent.com/deusdevok/ISLP_Python/main/Chapter%202/ex3curves.png

   **b)** Each term represent the Mean Squared Error of some term. The MSE is defined as $MSE=\frac{1}{n}\sum_{i=1}^n (y_i - \hat{f}(x_i))^2$.

   - **Bias (squared)**: The bias represent the error introduced by using a model that is not flexible enough for a given problem. For example, if the data shows a quadratic behaviour, trying to fit it with a linear function (small flexibility) will introduce a much bigger error than fitting with a poynomial of degree 2 (higher flexibility).
   - **Variance**: It represents the amount that $\hat{f}$ would change if we used a different training set. Using a different training data set should not change the variance too much. Increasing the model flexibility will generate a higher variance.
   - **Bayes (irreducible)**: The variance of the $\epsilon$ terms. $\epsilon$ is a random error term which has mean zero. The relashionship between the response $Y$ and the predictors $X$ can be written as $Y=f(X) + \epsilon$.
   - **Test error**: The sum of the Bias (squared), Variance and Irreducible errors. It is the expectation value of the difference between $y_0$ and $\hat{f}(x_0)$. That is, the expected MSE (Mean Squared Error) at $x_0$.
   - **Training error**: The MSE on the training data set. As the model flexibility increases, the error in the training set should decrease. The model learns about the variations in the training set as the model flexibility increases, but the prediction on the test set would begin to fail, making the test error increase (which is the one we want to reduce).

4. Real life applications for statistical learning.
   **a)** Classification
   - The data consists of a set of cats and dogs images. The goal is to predict weather a new image can be classified as a cat or a dog. The response can be a categorical variable (cat / dog). The predictors are each of the images in the training set (each image should be encoded somehow). The goal of this application is prediction.
   - The data consists of a table with information about page visitors, such as age, location, gender, education, interests and which ad the visitor had clicked on (furniture sales page, tech blog, news, etc). We wish to predict what type of ad should be shown to the visitor given the predictors. The response is the type of ad. The goal is prediction.
   - The data consists of employee satisfaction in a tech company. The features are age, position (CEO, junior developer, senior developer, etc), gender, years of experience, satisfaction (a number between 1 and 5). The goal is to understand which factors affect satisfaction. The goal of this application is inference.

   **b)** Regression
   - The data consists of employee information in different companies. For example, age, location, level of education, level of English, position (tech, HR, etc) and salary. The goal is to predict the salary. Since salary is a continuous variable, the problem falls in the regression category. 
   - The data consists of citizen features like name, age, city, country, level of education, has debts, and a credit score. The goal is to predict the credit score (a continuous variable).
   - The data consists of employee info (like the first example), but in this case the goal is to understand which factors affect salary. In this case, the goal of the application is inference.

   **c)** Cluster analysis
   - The data consists of two columns $X_1$ and $X_2$. No information about them is provided. We want to see if the data can be separated into different groups.
   - We have customer data like name, age, location, occupation, etc. We want to see if they can be grouped somehow.
   - The data consists of different characteristics of animals like weight, carnivore or hervivore, height, etc. We can see if they can be grouped in some way. Maybe we can infer if they fly or not, or if the can be pets or not, etc.

5. Model flexibility is the ability that the model can predict the complexities of a given data set. The more complex the data is, a more flexible model can predict it better. If a data set exhibits, for example, quadratic behaviour and we try to use a model that is too flexible, we might overfit the data, in which case new instances can be wrongly predicted. In contrast, if the data exhibits a more complex relashionship like a polynomial of degree 5, and we try to fit it with a linear function, we will underfit.

6. Parametric models are useful when the data exhibits a somewhat clear functional form (like linear). In this case it is easier to make a fit, since the problem reduces to find the corresponding parameters. A disadvantage of this method is that the true functional form is not always obvious, specially if the number of features is too large. Non-parametric models avoid the problem of infering the true relashionship of the data, but in order to make this work we need a lot more data compared to parametric models.

7. Table with data:
   
   | Obs | $X_1$ | $X_1$ | $X_1$ | $Y$ |
   |-|-|-|-|-|
   |1| 0 | 3 | 0 | Red |
   |2| 2 | 0 | 0 | Red |
   |3| 0 | 1 | 3 | Red |
   |4| 0 | 1 | 2 | Green |
   |5| -1 | 0 | 1 | Green |
   |6| 1 | 1 | 1 | Red |

   We want to predict $Y$ when $X_1=X_2=X_3=0$ using K-nearest neighbours.

   a) Euclidean distance between each observation and the test point.

   $d=\sqrt{(X-X_1)^2+(X-X_2)^2+(X-X_3)^2}$

   | Obs | d |
   | - | - |
   | 1 | 3 |
   | 2 | 2 |
   | 3 | $\sqrt{10} = 3.16$ |
   | 4 | $\sqrt{5} = 2.24$ |
   | 5 | $\sqrt{2} = 1.41$ |
   | 6 | $\sqrt{3} = 1.73$ |
   
   b) The prediction with $K=1$ would be *Green*. We have to look the one point that is closest to $(0,0,0)$, which is the $(-1,0,1)$ corresponding to the observation 5.

   c) With $K=3$ the prediction would be *Red*. The three points that are closest to $(0,0,0)$ are the instances 5, 6 and 2, which belong to *Green*, *Red* and *Red* respectively. The probability for *Green* is $1/3$ and for *Red* is $2/3$, and *Red* has a higher probability.

   d) If the Bayes decision boundary is highly non-linear, it means that the problem needs a high flexible model. We need a *low* value of $K$, because the lower $K$ is, the model would have higher flexibility.