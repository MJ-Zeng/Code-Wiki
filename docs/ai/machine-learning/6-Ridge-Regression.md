# Ridge Regression
## 1.Introducion
- The optimization problem turns to be
$$
\begin{align*}
\hat{\mathbf{w}} &= \arg \min_{\mathbf{w}} \sum_{i=1}^{n}(y_i - w_0 - w_1x_1 - \cdots - w_p x_p)^2 + \lambda \| \mathbf{w} \|_2^2 \\
&= \arg \min_{\mathbf{w}} \| \mathbf{y} - \mathbf{X}\mathbf{w} \|_2^2 + \lambda \| \mathbf{w} \|_2^2
\end{align*}
$$

- $\lambda \geq 0$ is a fixed parameter which has to be tuned by cross-validation.
- Equivalent to the constraint minimization problem:
$$
\hat{\mathbf{w}} = \arg \min_{\mathbf{w}} \| \mathbf{y} - \mathbf{X}\mathbf{w} \|_2^2 
 ,subject to \|\mathbf{w} \| \geq \mu
$$
where $\mu \geq 0$ is a prescribed threshold

- The larger $\lambda$ corresponds to the small $\mu$.

## 2.Solving Ridge Regression
$$
\begin{align*}
\hat{\mathbf{w}} &= \arg \min_{\mathbf{w}} \| \mathbf{y} - \mathbf{X}\mathbf{w} \|_2^2 + \lambda \| \mathbf{w} \|_2^2   \\
                 &= (\mathbf{Y} - \mathbf{X}\mathbf{W})^T(\mathbf{Y} - \mathbf{X}\mathbf{W}) + \lambda \| \mathbf{w} \|_2^2 \\
                 &= \mathbf{Y}^T\mathbf{Y} - \mathbf{Y}^T\mathbf{X}\mathbf{W} - \mathbf{W}^T\mathbf{X}^T\mathbf{Y} + \mathbf{W}^T\mathbf{X}^T\mathbf{X}\mathbf{W}  + \lambda\mathbf{W}^T\mathbf{W} \\  
\frac{\partial RSS}{\partial W} &= 0 - 2\mathbf{X}^T\mathbf{Y} + 2\mathbf{X}^T\mathbf{X}\mathbf{W} + 2\lambda I \mathbf{W} \\
                                &= -\mathbf{X}^T\mathbf{Y} + (\mathbf{X}^T\mathbf{X}\ + \lambda I)\mathbf{W}    \\
   \mathbf{W}     &= (\mathbf{X}^T\mathbf{X}\ + \lambda I)^{-1}\mathbf{X}^T\mathbf{Y}      \\
\end{align*}
$$

- Easy to show that $\mathbf{W}^{ridge} = (\mathbf{X}^T\mathbf{X}\ + \lambda I)^{-1}\mathbf{X}^T\mathbf{Y}$
- The estimator is also a projection of $\mathbf{y}$:
- 
  $$
  \mathbf{Y}^{ridge} = \mathbf{X}(\mathbf{X}^T\mathbf{X}\ + \lambda I)^{-1}\mathbf{X}^T\mathbf{Y}
  $$
  
- $\mathbf{X}$ can be diagonalized by SVD:$\mathbf{X} = \mathbf{PDQ}$ with $D = diag(v_1,\dots,v_{p+1})$,and $\mathbf{P} \in \mathbf{R}^{n \times (p+1)},\mathbf{Q} \in \mathbf{R}^{(p+1) \times (p+1)}$ being orthogonal matrices.
 $$\mathbf{Y}^{ridge} = \mathbf{P}diag(\frac{v_1^2}{v_1^2+\lambda},\dots,\frac{v_{p+1}^2}{v_{p+1}^2+\lambda})$$

- In the spectral space,the ridge regression estimator is a shrinkage of the OLS estimator($\lambda$ = 0))

## 3. Bayesian Viewpoint of Ridge Regression

- Given $\mathbf{X}$  and  $\mathbf{w}$,the conditional distribution of $\mathbf{y}$ is
  $$
  P(\mathbf{y}|\mathbf{X},\mathbf{w}) = N(\mathbf{Xw},\sigma^2\mathbf{I}) \propto exp(-\frac{1}{2\sigma^2}(\mathbf{y} - \mathbf{Xw})^T(\mathbf{y} - \mathbf{Xw}))
  $$
 - In addition,assume $\mathbf{w}$ has a prior distribution
   $$
   P(\mathbf{w}=N(\mu,\Lambda_0)) \propto exp(-\frac{1}{2}(\mathbf{w}-\mu)^T\Lambda_0^{-1}(\mathbf{w}-\mu))
   $$

- By Bayes theorem,the posterior distribution of $\mathbf{w}$ given the data $\mathbf{X}$ and y is
$$
\begin{align*}
    P(\mathbf{w} | \mathbf{X}, \mathbf{y}) &\propto P(\mathbf{y} | \mathbf{X}, \mathbf{w}) P(\mathbf{w}) \\
    &\propto \exp \left( -\frac{1}{2\sigma^2} (\mathbf{w}^T \mathbf{X}^T \mathbf{X} \mathbf{w} - 2 \mathbf{y}^T \mathbf{X} \mathbf{w}) \right) \\
    &\propto \exp \left( -\frac{1}{2\sigma^2} (\mathbf{w}^T \mathbf{X}^T \mathbf{X} \mathbf{w} - 2 \mathbf{y}^T \mathbf{X} \mathbf{w}) \right. \\
    &\qquad \left. - \frac{1}{2} (\mathbf{w}^T \boldsymbol{\Lambda}_0^{-1} \mathbf{w} - 2 \boldsymbol{\mu}_0^T \boldsymbol{\Lambda}_0^{-1} \mathbf{w}) \right) \\
    &= \exp \left( -\frac{1}{2} (\mathbf{w} - \boldsymbol{\mu}_m)^T \boldsymbol{\Lambda}_m^{-1} (\mathbf{w} - \boldsymbol{\mu}_m) \right)
\end{align*}
$$


- If $\boldsymbol{\mu}_0 = \mathbf{0}$ and $\boldsymbol{\Lambda}_0 = \frac{\sigma^2}{\lambda} \mathbf{I}_{p+1}$, then $\hat{\mathbf{w}} = \boldsymbol{\mu}_m = \left( \mathbf{X}^T \mathbf{X} + \lambda \mathbf{I}_{p+1} \right)^{-1} \mathbf{X}^T \mathbf{y}$ maximizes the posterior probability $P(\mathbf{w} | \mathbf{X}, \mathbf{y})$.

## 4.Ridge Trace
- The function plot of $\mathbf{W}(\lambda)$ with $\lambda$ is called ridge trace.
- The large variations in ridge trace indicate the multicolinearity in variables.
- when $\lambda \in$(0,0.5),the ridge traces have large variations,it suggests to choose $\lambda$ = 1.


![](https://files.mdnice.com/user/75397/540d6281-3c36-4430-88f4-51dd775488c4.png)


## 5.Exercise





```python
import numpy as np
from sklearn.preprocessing import PolynomialFeatures

# 原生实现
class RidgeRegression:
    def __init__(self, alpha=1.0, degree=1):
        self.alpha = alpha
        self.weights = None
        self.degree = degree
        self.poly = PolynomialFeatures(degree=self.degree, include_bias=False)

    def _add_intercept(self, X):
        '''偏置项b'''
        return np.c_[np.ones(X.shape[0]), X]

    def fit(self, X, y):
        X_poly = self.poly.fit_transform(X)
        X_poly = self._add_intercept(X_poly)
        self.weights = np.linalg.inv(X_poly.T @ X_poly + self.alpha * np.eye(X_poly.shape[1])) @ X_poly.T @ y

    def predict(self, X_test):
        X_test_poly = self.poly.transform(X_test)
        X_test_poly = self._add_intercept(X_test_poly)
        return X_test_poly @ self.weights


    def score(self, X, y_true):
        y_pred = self.predict(X)
        sse = np.sum((y_true - y_pred) ** 2)
        sst = np.sum((y_true - y_true.mean()) ** 2)
        r_square = 1 - sse / sst
        return r_square

    def get_weights(self):
        return self.weights

```


```python
import numpy as np
from sklearn.model_selection import train_test_split
import matplotlib.pyplot as plt

# 生成数据
x = np.linspace(0, 1, 1000)
y = np.sin(2 * np.pi * x)
y = [np.random.normal(0, 0.1) + y_i for y_i in y]

# 将数据转换为 NumPy 数组
x = np.array(x).reshape(-1, 1)  # 转换为二维数组，形状为 (10, 1)
y = np.array(y).reshape(-1, 1)  # 转换为二维数组，形状为 (10, 1)

# 划分训练和测试数据
X_train, X_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=42)

```


```python
## Ridge Trace
alphas = np.logspace(-12, -5, 1000)
weights_list = []
for alpha in alphas:
    ridge_reg = RidgeRegression(alpha=alpha,degree=9)
    ridge_reg.fit(X_train, y_train)
    weights = ridge_reg.get_weights()
    weights_list.append(weights)

weights_array = np.array(weights_list)

plt.figure(figsize=(10, 6))
for i in range(weights_array.shape[1]):
    plt.plot(alphas, weights_array[:, i], label=f'weight_{i}')

plt.xscale('log')
plt.xlabel('Alpha')
plt.ylabel('Weights')
plt.title('Ridge Trace')
plt.legend()
plt.grid(True)
plt.show()  
    
```


    

![](https://files.mdnice.com/user/75397/fe26b7b2-1539-4326-873a-a9679aed76d7.png)

    



```python
# 训练模型
ridge_reg = RidgeRegression(alpha=10**-6,degree=9)
ridge_reg.fit(X_train, y_train)

# 预测
y_train_pred = ridge_reg.predict(X_train)
y_test_pred = ridge_reg.predict(X_test)

# 评估模型
train_score = ridge_reg.score(X_train, y_train)
test_score = ridge_reg.score(X_test, y_test)

print(f"Train R^2 Score: {train_score}")
print(f"Test R^2 Score: {test_score}")

# 生成用于绘制的点
x_points = np.linspace(0, 1, 1000).reshape(-1, 1)
y_points_pred = ridge_reg.predict(x_points)

# 绘制原始数据、训练数据、测试数据和预测曲线
plt.figure(figsize=(10, 6))
plt.scatter(x, y, label='Original Data with Noise', color='blue')
plt.scatter(X_train, y_train, label='Training Data', color='red')
plt.scatter(X_test, y_test, label='Testing Data', color='green')
plt.plot(x_points, y_points_pred, label='Predicted Curve', color='black')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.show()
```

    Train R^2 Score: 0.9792995743595913
    Test R^2 Score: 0.9805271411400318
    


    

![](https://files.mdnice.com/user/75397/1fa6ff66-5bff-40b8-86ca-c8895695f3bd.png)

    


## 5.Reference
- https://github.com/zhangzsustech/machinelearning
