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