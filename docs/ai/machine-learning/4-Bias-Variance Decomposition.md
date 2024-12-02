## 1.Bias-Variance Decomposition

- Bias-variance decomposition of gnerlization error in $L^2$ loss:
$$
E_{train}R_{exp}(\hat{f}(x))=E_{train}E_P[(y-\hat{f}(x))^2|x]=\underbrace{\operatorname{Var}(\hat{f}(x))}_{\text{variance}}+\underbrace{\operatorname{Bias}^2(\hat{f}(x))}_{\text{bias}}+\underbrace{\sigma^2}_{\text{noise}}
$$
where $P=P(y|x)$ is the conditional probability of y given x

- Bias:$Bias(\hat{f}(x)) = E_{train}\hat{f}(x)-f(x)$ is the average accuracy of prediction for the model(deviation from the truth)
- Variance:$Var(\hat{f}(x))=E_{train}（\hat{f}(x)-E_{train}\hat{f}(x))^2$ is the variability of the model prediction due to the different data set(stability)


## 2.Different Combinations of Bias-Variance
There can be four combinations between bias and variance.

- **High Bias, Low Variance:** underfitting.
- **High Variance, Low Bias:** overfitting.
- **High-Bias, High-Variance:**  the model is not able to capture the underlying patterns in the data 
- **Low Bias, Low Variance:**   the ideal scenario for a machine learning model

![](https://files.mdnice.com/user/75397/20cbd134-040a-481b-8d59-f3eda7f7e2e3.png)

## 3.Bias Variance Tradeoff
- An algorithm can’t be more complex and less complex at the same time. For the graph, the perfect tradeoff will be like this.

![](https://files.mdnice.com/user/75397/26046d85-6c78-4b00-9216-cb50e8c7ffc2.png)

## 4.Mathematical Derivation for total error
The Mean Squared Error (MSE) can be decomposed as follows:


$$
\begin{aligned}
\text{MSE} &= (Y - \hat{Y})^2 \\
           &= (Y - E(\hat{Y}) + E(\hat{Y}) - \hat{Y})^2 \\
           &= (Y - E(\hat{Y}))^2 + (E(\hat{Y}) - \hat{Y})^2 + 2(Y - E(\hat{Y}))(E(\hat{Y}) - \hat{Y}) \\
           &= (Y - E(\hat{Y}))^2 + (E(\hat{Y}) - \hat{Y})^2 + 2(Y - E(\hat{Y}))E[E(\hat{Y}) - \hat{Y}] \\
           &= (Y - E(\hat{Y}))^2 + (E(\hat{Y}) - \hat{Y})^2 + 2(Y - E(\hat{Y}))(0) & \quad \text{(since } E[E(\hat{Y}) - \hat{Y}] = 0\text{)} \\
           &= \text{Bias}^2 + \text{Variance}
\end{aligned}
$$ned}
$$
Here:
- $ Y $ is the true value.
- $ \hat{Y} $ is the predicted value.
- $ E(\hat{Y}) $ is the expected value of the predicted value.

## 5.Reference
- https://github.com/zhangzsustech/machinelearning
