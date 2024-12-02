# LASSO Regression
## 1.Introduction

- **Least Absolute Shrinkage and Selection Operator**.
- **Feature Selection**:By reducing the coefficients of less significant features to zero, Lasso regression automatically chooses a selection of features.
- **Collinearity**:By reducing the coefficients of correlated variables and choosing one, lasso regression might be useful when there is multicollinearity
- **Regularization**:By penalizing big coefficients, Lasso regression can aid in preventing overfitting.
- **Interpretability**

## 2. LASSO Formulation

- The optimization problem
  $$
  \hat{\mathbf{w}} = \arg\min_wE(W)
  $$
  $$
    E(\mathbf{w}) = \| \mathbf{y} - \mathbf{Xw} \|_2^2 + \lambda \|\mathbf{w}\|_1
  $$
  - Equivalent to the constriant minimization problem:
    $$
        \mathbf{w} = \| \mathbf{y} - \mathbf{Xw} \|_2^2 
    $$
    $Subject to \|\mathbf{w}\|_1 \leq \mu$
  - The large $\lambda$ corresponds to the small $\mu$.
  - The optimal solution is sparse with   $\mathbf{w_2}$ = 0.

![](https://files.mdnice.com/user/75397/220f80ed-863c-4d14-aecd-53a0402c37ab.png)

## 3. Solving LASSO Regression

- Linear regression:
    - $$
      \begin{align*}
          RSS(W) &= [y-XW]^T[y-XW] \\
                 &= y^Ty-y^TXW-W^TX^Ty+W^TX^TXW  \\
                 &= y^Ty-2y^TXW+W^TX^TXW   \\
      \end{align*}
      $$
    - $$\frac{\partial RSS}{\partial w}=0-2y^TX+2X^TXW=0$$

- Assume $\mathbf{X}^T\mathbf{X} = \mathbf{I}_{p+1}$,then $\hat{\mathbf{OLS}}=\mathbf{X}^T\mathbf{y}$.
- $\partial_w \mathbf{E(W)} = \mathbf{w-X^Ty}$ + $\lambda(\partial|w_0| \times \dots \times \partial|w_p|)$.
- If $\hat{w_i^{lasso}}$ < 0, $\partial{|w_i^{lasso}|}$ = {-1},and $w_i^{lasso} = w_i^{OLS} + \lambda$ with $w_i^{OLS} < -\lambda$.
-  If $\hat{w_i^{lasso}}$ > 0, $\partial{|w_i^{lasso}|}$ = {1},and $w_i^{lasso} = w_i^{OLS} - \lambda$ with $w_i^{OLS} > \lambda$.
- If $\hat{w_i^{lasso}}$ = 0, $\partial{|w_i^{lasso}|}$ = [-1,1],and $w_i^{lasso} = w_i^{OLS} - \lambda$ with $w_i^{OLS} \in [-\lambda,\lambda]$.

- In summary, $\hat{w_i^{lasso}} = max(|w_i^{OLS} - \lambda|,0) + sign(w_i^{OLS})$.

![](https://files.mdnice.com/user/75397/22ce617f-54ae-48c5-99a4-5beaecccd35d.png)


### 3.1 Coordinate Descent for Lasso Regression

The objective function of Lasso regression is given by:

$ \min_{\beta} \frac{1}{2n} \| y - X\beta \|_2^2 + \alpha \| \beta \|_1 $

where:
- $ y $ is the target variable vector.
- $ X $ is the feature matrix.
- $ \beta $ is the weight vector.
- $ \alpha $ is the regularization parameter.
- $ \| \cdot \|_2^2 $ denotes the squared Euclidean norm.
- $ \| \cdot \|_1 $ denotes the L1 norm.

#### **Coordinate Descent Algorithm**

The coordinate descent algorithm updates each weight $ \beta_j $ while keeping all other weights fixed. The steps are as follows:

1. **Initialize** all weights to zero: $ \beta = \mathbf{0} $.
2. **Iterate** over each feature $ j $:
   $$
   \beta_j = \text{soft\_threshold}\left( \frac{\sum_{i=1}^{n} (y_i - \sum_{k \neq j} \beta_k x_{ik}) x_{ij}}{n}, \frac{\alpha}{n} \right)
   $$
   where:
   $$
   \text{soft\_threshold}(a, b) = \text{sign}(a) \cdot \max(|a| - b, 0)
   $$
3. **Repeat** step 2 until convergence.

#### Soft Thresholding Function

The soft thresholding function is defined as:

$ \text{soft\_threshold}(a, b) = \begin{cases} 
a - b & \text{if } a > b \\
0 & \text{if } |a| \leq b \\
a + b & \text{if } a < -b 
\end{cases} $

This can also be written more compactly as:

$ \text{soft\_threshold}(a, b) = \text{sign}(a) \cdot \max(|a| - b, 0) $

where:
- $\text{sign}(a)$ is the sign function, which returns $1$ if $a > 0$, $-1$ if $a < 0$, and $0$ if $a = 0$.
- $\max(|a| - b, 0)$ computes the maximum value between $|a| - b$ and $0$.

#### **Pseudocode**

```plaintext
Algorithm: Coordinate Descent for Lasso Regression
Input: Feature matrix X, Target vector y, Regularization parameter alpha, Number of iterations n_iterations, Tolerance tol
Output: Weight vector beta

1. Initialize beta to zeros: beta <- 0
2. Set n to number of samples
3. Set n_features to number of features
4. For iteration from 1 to n_iterations do:
     a. Set beta_old to beta
     b. For j from 1 to n_features do:
          i. Compute residuals: residuals <- y - sum(beta[k] * X[:, k] for k != j)
          ii. Compute rho: rho <- (1/n) * sum(residuals[i] * X[i, j] for i in range(n))
          iii. Compute z_j: z_j <- (1/n) * dot(X[:, j], X[:, j])
          iv. If z_j > 0 then:
               Update beta[j]: beta[j] <- soft_threshold(rho, alpha/n) / z_j
     c. If ||beta - beta_old||_1 < tol then:
          Break loop
5. Return beta

## 4. LASSO Path
- where $\lambda$ varies,the values of the coefficients form paths(regularization paths)
- The paths are piecewise linear with the same change points,may cross the x-axis many times.
- In practice,choose $\lambda$ by cross-validation.
  

![](https://files.mdnice.com/user/75397/4badf5a9-c4a8-42b7-be1e-51d14279f976.png)

## 5.Exercise


```python
import numpy as np
from sklearn.preprocessing import PolynomialFeatures

class LassoRegression:
    '''目前还未解决溢出问题'''
    def __init__(self, alpha=1.0, degree=1, n_iterations=1000, tol=1e-4):
        self.alpha = alpha
        self.degree = degree
        self.n_iterations = n_iterations
        self.tol = tol  # 停止准则的阈值
        self.weights = None
        self.poly = PolynomialFeatures(degree=self.degree, include_bias=False)

    def _add_intercept(self, X):
        return np.c_[np.ones((X.shape[0], 1)), X]

    def _soft_thresholding(self, a, b):
        """Soft thresholding operator."""
        return np.sign(a) * np.maximum(np.abs(a) - b, 0)

    def fit(self, X, y):
        X_poly = self.poly.fit_transform(X)
                
        # 添加截距项
        X_poly = self._add_intercept(X_poly)
        
        n_samples, n_features = X_poly.shape
        self.weights = np.zeros(n_features)
        
        for iteration in range(self.n_iterations):
            weights_old = self.weights.copy()
            for j in range(n_features):
                # 计算残差（排除第j个特征）
                residuals = y - (X_poly @ self.weights - self.weights[j] * X_poly[:, j])
                # 计算rho和z_j
                rho = np.sum(residuals * X_poly[:, j]) / n_samples  
                z_j = (X_poly[:, j].T @ X_poly[:, j]) / n_samples
                
                # 更新权重
                if z_j > 1e-5:  # 防止除零错误
                    self.weights[j] = self._soft_thresholding(rho, self.alpha) / z_j
            
            # 检查是否收敛
            if np.linalg.norm(self.weights - weights_old, ord=1) < self.tol:
                break

    def predict(self, X):
        X_poly = self.poly.transform(X)
        X_poly = self._add_intercept(X_poly)
        return X_poly @ self.weights

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
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.linear_model import Lasso

# 创建简短的合成数据集
np.random.seed(42)
X = np.random.rand(100, 2)  # 100个样本，每个样本有2个特征
y = 3 * X[:, 0] + 2 * X[:, 1] + np.random.randn(100) * 0.5  # 目标变量是线性组合加上一些噪声

# 数据标准化
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# 划分训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)

# 创建并训练Lasso回归模型
lasso = LassoRegression(alpha=1e-2,degree=1, n_iterations=1000, tol=1e-5)
lasso.fit(X_train, y_train)

# 预测
y_pred = lasso.predict(X_test)

# 评估模型
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"Mean Squared Error: {mse:.2f}")
print(f"R^2 Score: {r2:.2f}")

# 打印权重
weights = lasso.get_weights()
print("Model Weights:", weights)

# 绘制预测结果图
def plot_predictions(y_true, y_pred):
    """绘制预测结果图"""
    plt.figure(figsize=(8, 6))
    plt.scatter(y_true, y_pred, label='Predicted vs True')
    
    # 添加回归线
    fit = np.polyfit(y_true, y_pred, deg=1)
    y_fit = fit[0] * y_true + fit[1]
    plt.plot(y_true, y_fit, color='red', linestyle='--', label='Regression Line')
    
    plt.plot([min(y_true), max(y_true)], [min(y_true), max(y_true)], color='green', linestyle='-', label='Perfect Prediction')
    
    plt.xlabel('True Values')
    plt.ylabel('Predicted Values')
    plt.title('True vs Predicted Values')
    plt.legend()
    plt.show()

# 绘制预测结果
plot_predictions(y_test, y_pred)
```

    Mean Squared Error: 0.18
    R^2 Score: 0.81
    Model Weights: [2.44233145 0.94131646 0.62582496]
    


    

![](https://files.mdnice.com/user/75397/6105e574-7c23-460e-8de8-e8525282de03.png)
    

