# Chapter 2 Summary

## Bias Variance Trade Off

In the following proof I will be using a formula relating variance with expected values:

$$Var(X)=E(X^2)-E^2(X)$$

The beginning of the proof starts by considering the expectation value of the difference between $Y$ and $\hat{Y}$:

$$E[(Y-\hat{Y})]=E[Y^2-2Y\hat{Y}+\hat{Y}^2]$$

$$E[(Y-\hat{Y})]=E[Y^2]-2E[Y\hat{Y}]+E[\hat{Y}^2]$$

### Solving each term:

* $E[\hat{Y}^2]$
  
  $$E[\hat{Y}^2]=Var(\hat{Y})+E^2[\hat{Y}]$$

* $E[Y^2]$

  Since $Y=f+\epsilon$

  $$E[Y^2]=E[(f+\epsilon)^2]=E[f^2]+2E[f\epsilon]+E[\epsilon^2]$$

  Since $f$ doesn't depend on the data ($f$ is deterministic): $E[f] = f$, $E[f^2]=f^2$, $Var(f)=0$, etc.

  $$E[Y^2]=f^2+2fE[\epsilon]+E[\epsilon^2]$$

  The error $\epsilon$ has zero mean, $E[\epsilon]=0$. Let's call $E[\epsilon^2]=\sigma^2$:

  $$E[Y^2]=f^2+\sigma^2$$

* $E[Y\hat{Y}]$
  
  $$E[Y\hat{Y}]=E[(f+\epsilon)\hat{Y}]=E[f\hat{Y}+\epsilon\hat{Y}]$$

  Since $\hat{Y}$ and $\epsilon$ are independent:

  $$E[Y\hat{Y}]=E[f\hat{Y}]+E[\epsilon]E[\hat{Y}]$$

  Use that $E[\epsilon]=0$, and $f$ is independent of the data (as used before):

  $$E[Y\hat{Y}]=fE[\hat{Y}]$$

We have now all three terms. Putting all together:

$$E[(Y-\hat{Y})^2]=Var(\hat{Y})+E^2[\hat{Y}]+f^2+\sigma^2-2fE[\hat{Y}]$$

$$\boxed{E[(Y-\hat{Y})^2]=(f-E[\hat{Y}])^2+Var(\hat{Y})+\sigma^2}$$

Where $(f-E[\hat{Y}])^2$ is called the *Bias*.