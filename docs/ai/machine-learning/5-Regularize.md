# 1.Regularization by Subset Selection

- In high dimensions,the more the input attributes,the larger the variance.
- Shrinking some coefficients or setting them to zero can reduce the overfitting.
- Using less input variables also help interpreetation with the most important variables.
- Subset selection:retaining only a subset of the variables,while eliminating the rest variables from model.
- Best-Subset selection:Find for each k $\in{0,1,\dots,p}$ the subset $S_k \subseteq {0,1,\dots,p}$ of size k that gives the smallest RSS(W)

## 2.Best-Subset Selection
- The best subset of size k + 1 may not include the the variables in the best subset of size k
- The RSS of the best subset of size k is not necessarily decreasing with k
- Choose k based on bias-variance tradeoff, usually by AIC and BIC, or practically by cross-validation

![](https://files.mdnice.com/user/75397/5868891a-641e-4a74-a8f5-ba9ee69418fa.png)

- **Forward-Stagewise (FS) Selection**:
    - At each step, identify the variables (among all variables) most correlated with the current residual,
    - then regress the residual on this chosen variable and increment the current coefficient with the new regression coefficient
      
- **Backward-stepwise selection**:
    - start with the full model,
    - then sequentially delete from the model the variables that has the least impact on the fit most (the candidate for dropping is the variable with the smallest Z-score) ;
    - can only be used when n > p in order to fit the full model by OLS


![](https://files.mdnice.com/user/75397/edb3bb51-7991-446c-b9f2-f73f4ded5e97.png)

## 3.Reference
- https://github.com/zhangzsustech/machinelearning
