# 一.Univariate Linear Regression

- Linear model:$y=w_0+w_1x+\varepsilon$,where $w_0$ and $w_1$ are regression coefficients,$\varepsilon$ is the error or noise
- Assume $\varepsilon \sim N(0,\sigma^2)$,where $\sigma^2$ is a fixed but unknow variance;the $y_i|x_i \sim N(W_0+W_1x_i,\sigma^2)$
- Assume the samples ${x_i,y_i}_{i=1}^n $ are generated from this conditional distribution,i.e.,$y_i|x_i \sim N(W_0+W_1x_i,\sigma^2)$
- Inuitively,find the best straight line($w_0$ and $w_1$) such that the sample points fit it well,i.e..,the residuals are minimized.
$$ (\hat{w_0},\hat{w_1}) = \arg \min_{w_0,w_1} \sum_{i=1}^{n} (y_i - w_0 - w_1x_i)^2 $$


![](https://files.mdnice.com/user/75397/0407fdeb-9147-4872-ab01-10ea159db537.png)


## 二、Multivariate Linear Model


A linear model can be represented as:

$$ y = f(x) + \epsilon = w_0 + w_1 x_1 + \cdots + w_p x_p + \epsilon $$

where,

- $w_0, w_1, \ldots, w_p$ are regression coefficients,
- $x = (x_1, \ldots, x_p)^T$ is the input vector whose components are independent variables or attribute values,
- $\epsilon \sim \mathcal{N}(0, \sigma^2)$ is the noise.

For the size $n$ samples $\{(x_i, y_i)\}_{i=1}^{n}$, let $y = (y_1, \ldots, y_n)^T$ be the response or dependent variables, $w = (w_0, w_1, \ldots, w_p)^T$, $\mathbf{X} = [1_n, (x_1, \ldots, x_n)^T] \in \mathbb{R}^{n \times (p+1)}$, and $\varepsilon = (\varepsilon_1, \ldots, \varepsilon_n)^T \sim \mathcal{N}(0, \sigma^2 I_n)$.

$$ y = Xw + \varepsilon $$

$$
\begin{align}
X &= 
\begin{pmatrix}
1 & x_{11} & \dots & x_{1p} \\
1 & x_{21} & \dots & x_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
1 & x_{n1} & \dots & x_{np}
\end{pmatrix} \\
&= 
\begin{pmatrix}
1_n \\
\mathbf{x}_1 \\
\vdots \\
\mathbf{x}_n
\end{pmatrix}
\end{align}
$$



![](https://files.mdnice.com/user/75397/5c9568c1-b9c1-4c9c-afc6-364fe6105cbf.png)


### 2.1 Least Square
- Minimizing the Total Residual Sum-of-Squares (RSS)：

$$RSS(w) = \sum_{i=1}^{n}{(y_i - w_0 - w_1 x_{1i} - \cdots - w_p x_{pi})^2} = ||y - Xw||_2^2$$

- When $X^TX$ is invertible, the minimizer $\hat{w}$ satisfies:
$$\nabla_w RSS(\hat{w}) = 0 \quad \Rightarrow \quad \hat{w} = (X^TX)^{-1}X^Ty$$

- The prediction $\hat{y} = X(X^TX)^{-1}X^Ty = Py$ represents a projection of $ y $ onto the linear space spanned by the column vectors of $ X $. Here, $ P = X(X^TX)^{-1}X^T $ is the projection matrix satisfying $P^2 = P $.


![](https://files.mdnice.com/user/75397/eebfa8ba-d015-48b7-acec-9bd2f2b7790d.png)




## 2.2 Maximal Likelihood Estimate

- A probabilistic viewpoint:

$$
y | \mathbf{x} \sim N(w_0 + w_1 x_1 + \cdots + w_p x_p, \sigma^2)
$$

- Likelihood Function：

$$
L(\mathbf{w}; \mathbf{X}, y) = P(y|\mathbf{X}, \mathbf{w}) = \prod_{i=1}^{n} P(y_i|\mathbf{x}_i, \mathbf{w}) 
$$ 

$$ 
P(y_i|\mathbf{x}_i, \mathbf{w}) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y_i - w_0 - w_1 x_{1i} - \cdots - w_p x_{pi})^2}{2\sigma^2}}
$$

- Maximal likelihood estimate: given the samples from some unknown parametric distribution, find the parameters such that the samples most probably seem to be drawn from that distribution, i.e.,
$$ 
\hat{\mathbf{w}} = \arg\max_{\mathbf{w}} L(\mathbf{w}; \mathbf{X}, y) 
$$

- Log-Likelihood Function：


$$ 
l(\mathbf{w}; \mathbf{X}, y) = \log L(\mathbf{w}; \mathbf{X}, y) = - n \log(\sqrt{2\pi}\sigma) - \frac{1}{2\sigma^2} \sum_{i=1}^{n} (y_i - w_0 - w_1 x_{1i} - \cdots - w_p x_{pi})^2 
$$


- The same minimizer as LS: $ \hat{\mathbf{w}} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top y $


## 2.3  Shortcoming

Multicollinearity

- If the columns of $X$ are almost linearly dependent, i.e., multicollinearity, then det($X^TX$) ≈ 0, the diagonal entries in ($X^TX$).inv() get quite large.
  This implies the variances of $\hat w$ get large, and the estimate is not accurate.

Example
- 10 samples are drawn from the true model $y = 10 + 2^x_1 + 3^x_2 + \epsilon$
- The LS estimator is $\hat w_0 = 11.292, \hat w_1 = 11.307, \hat w_2 = -6.591$, far from the true coefficients
- Correlation coefficient is $r_{12 = 0.986$

Remedies
- Ridge regression
- Principal component regression
- Partial least squares regression, etc.

## 2.4 使用最小二乘法拟合曲线
- 举例：我们用目标函数$y=sin2\pi x$
, 加上一正态太分布的噪音干扰，用多项式去拟合$


```python
import numpy as np
import scipy as sp
from scipy.optimize import least_squares
import matplotlib.pyplot as plt

def real_func(x):
    return np.sin(2*np.pi*x)

def fit_fun(p,x):
    f=np.poly1d(p)
    return f(x)

def residual_func(p,x,y):
    return fit_fun(p,x)-y


x = np.linspace(0,1,10)
x_points = np.linspace(0,1,1000)

y=real_func(x)
y= [np.random.normal(0,0.1)+y_i for y_i in y]

def fitting(M=0,resid_func = residual_func):
    p_init = np.random.rand(M+1)

    p_lsq = least_squares(resid_func,p_init,args=(x,y))
    print('Fitting Parameters:', p_lsq.x)

    plt.plot(x_points,real_func(x_points),label='real')
    plt.plot(x_points,fit_fun(p_lsq.x,x_points),label='fit')
    plt.plot(x,y,'bo',label='noise')
    plt.title(f'M={M}')
    plt.show()
    
     
```


```python
for m  in range(10):  
    fitting(M=m)
```

    Fitting Parameters: [0.08601442]
    


    

![](https://files.mdnice.com/user/75397/8dbfb5f2-cfba-4aa0-b92c-6f4d19430c85.png)

    


    Fitting Parameters: [-1.23011084  0.70106984]
    


    

![](https://files.mdnice.com/user/75397/abc5a276-d42a-4522-953e-3fe8cf8f7e8c.png)

    


    Fitting Parameters: [ 0.1367554  -1.36686623  0.7213299 ]
    


    

![](https://files.mdnice.com/user/75397/f8063ef0-7e08-4d01-8784-3db27c003e08.png)

    


    Fitting Parameters: [ 22.14437188 -33.07980244  11.23628865  -0.04415456]
    


    

![](https://files.mdnice.com/user/75397/ffd6079c-eca0-4e42-b8d0-fb0a615116fe.png)

    


    Fitting Parameters: [ 7.43392282e+00  7.27652652e+00 -2.38103436e+01  9.40075232e+00
      4.79306608e-03]
    


    

![](https://files.mdnice.com/user/75397/576cfda5-5191-4ee2-8120-02c994a396e5.png)

    


    Fitting Parameters: [-4.23866636e+01  1.13400585e+02 -8.51717596e+01  8.89542032e+00
      5.47713692e+00  4.78624122e-02]
    


    

![](https://files.mdnice.com/user/75397/f4aa6784-47bb-4167-9255-1033b6609dbb.png)

    


    Fitting Parameters: [ 3.05429450e+01 -1.34015490e+02  2.16410158e+02 -1.38476205e+02
      2.12800090e+01  4.47330180e+00  5.16241930e-02]
    


    

![](https://files.mdnice.com/user/75397/88e2211b-1659-4631-bae5-8bbb237484f7.png)

    


    Fitting Parameters: [-2.43379444e+02  8.82372513e+02 -1.30781162e+03  1.02132410e+03
     -4.23144313e+02  6.92840081e+01  1.56409209e+00  5.43145507e-02]
    


    

![](https://files.mdnice.com/user/75397/7334d67d-90ca-4965-8115-1a41e19206e0.png)

    


    Fitting Parameters: [-3.55117384e+03  1.39613198e+04 -2.23186439e+04  1.85787820e+04
     -8.53079964e+03  2.10893510e+03 -2.66420951e+02  1.82108282e+01
      5.19883853e-02]
    


    

![](https://files.mdnice.com/user/75397/d329d6b7-f67d-4161-b9de-55e4c3077da3.png)

    


    Fitting Parameters: [ 4.92552325e+03 -2.57160303e+04  5.58551026e+04 -6.55108820e+04
      4.49567009e+04 -1.82130051e+04  4.16991475e+03 -4.95231436e+02
      2.81167937e+01  5.18934891e-02]
    


    

![](https://files.mdnice.com/user/75397/e9243096-5209-4cc4-93ae-5e6de4a61eed.png)

    


- 正则化

结果显示过拟合， 引入正则化项(regularizer)，降低过拟合

$$Q(x) = \sum_{i=1}^{n}(h(x_i) - y_i)^2 + \lambda ||w||^2.$$

回归问题中，损失函数是平方损失，正则化可以是参数向量的L2范数，也可以是L1范数。

- L1: regularization * abs(p)
- L2: 0.5 * regularization * np.square(p)


```python
regularization = 0.0001

def residuals_func_regularization(p, x, y):
    res = fit_fun(p,x)-y
    reg = 0.5 * regularization * np.sum(np.square(p))
    return np.append(res, reg)

fitting(M=9,resid_func=residuals_func_regularization)
```

    Fitting Parameters: [  0.29034077  -5.04787331  -3.88972388   4.35622674  13.91092879
      10.08414455 -16.43786885 -10.39724264   7.35888135   0.03420107]
    


    

![](https://files.mdnice.com/user/75397/105b5fb4-32df-4a81-b6e3-7e40554df51f.png)

# 参考
- 【大数据导论 - 26. Multivariate Linear Regression】 https://www.bilibili.com/video/BV1D7421d7BL/?share_source=copy_web&vd_source=6e11ed68441fc0c9914eaf702e472d72
    

