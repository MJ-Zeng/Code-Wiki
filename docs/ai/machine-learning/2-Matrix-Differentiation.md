# 矩阵求导

## 一、标量方程对向量的导数
- 标量：$f(y)$
- 向量：$\mathbf{y}=[y_1,y_2,\ldots,y_m]^T$

### 1.1 分母布局：
- 行数与分母相同
$$
\frac{\partial f(y)}{\partial y} = 
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\vdots \\
\frac{\partial f(y)}{\partial y_m}
\end{bmatrix}
$$

### 1.2 分子布局
- 行数与分子相同
$$
\frac{\partial f(y)}{\partial y} = \left[ \frac{\partial f(y)}{\partial y_1}, \frac{\partial f(y)}{\partial y_2}, \cdots, \frac{\partial f(y)}{\partial y_m} \right]
$$

### 1.3 例
- $f(y_1,y_2)=y_1^2+y_2^2$
- $\mathbf{y}=[y_1,y_2]^T$
- 分母布局
$$
\frac{\partial f(y)}{\partial \mathbf{y}}=
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\end{bmatrix}=
\begin{bmatrix}
2y_1 \\
2y_2 \\
\end{bmatrix}
$$

- 分子布局
$$
\frac{\partial f(y)}{\partial y} = \left[ \frac{\partial f(y)}{\partial y_1}, \frac{\partial f(y)}{\partial y_2}, \cdots, \frac{\partial f(y)}{\partial y_m} \right]
= [2y_1,2y_2]
$$

## 二、向量方程对向量的导数
- 标量：$f(y)=
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\vdots \\
\frac{\partial f(y)}{\partial y_n}
\end{bmatrix}=$
- 向量：$\mathbf{y}=[y_1,y_2,\ldots,y_m]^T$

### 2.1 分母布局
$$
\frac{\partial f(y)_{n×1}}{\partial \mathbf{y}_{m×1}}=
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\vdots \\
\frac{\partial f(y)}{\partial y_m} 
\end{bmatrix}=
\begin{bmatrix}
\frac{\partial f_1(y)}{\partial y_1} & \frac{\partial f_2(y)}{\partial y_1}  \cdots \frac{\partial f_n(y)}{\partial y_1} \\ 
\vdots & \ddots & \vdots \\
\frac{\partial f_1(y)}{\partial y_m} &  \cdots & \frac{\partial f_n(y)}{\partial y_m}
\end{bmatrix}_{m×n}
$$

### 2.1 分子布局
$$
\frac{\partial f(y)_{n×1}}{\partial \mathbf{y}_{m×1}}=
\left[ \frac{\partial f(y)}{\partial y_1}, \frac{\partial f(y)}{\partial y_2}, \cdots, \frac{\partial f(y)}{\partial y_m} \right]=
\begin{bmatrix}
\frac{\partial f_1(y)}{\partial y_1} & \frac{\partial f_1(y)}{\partial y_2}  \cdots \frac{\partial f_n(y)}{\partial y_m} \\ 
\vdots & \ddots & \vdots \\
\frac{\partial f_n(y)}{\partial y_1} & \cdots & \frac{\partial f_n(y)}{\partial y_m}
\end{bmatrix}_{n×m}
$$

### 2.3 举例
- $f(y)=
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\end{bmatrix}=
\begin{bmatrix}
y_1^2+ y_2^2+y_3\\
2y_1 + y_3^2  \\
\end{bmatrix}
$

- 向量：$\mathbf{y}=[y_1,y_2,y_3]^T$
- $\frac{\partial f(y)}{\partial \mathbf{y}}=
\begin{bmatrix}
\frac{\partial f(y)}{\partial y_1} \\
\frac{\partial f(y)}{\partial y_2} \\
\frac{\partial f(y)}{\partial y_3} 
\end{bmatrix}=
\begin{bmatrix}
2y_1 & 2 \\
2y_2 & 0 \\
1 & 2y_3
\end{bmatrix}
$

### 2.4 常用特例
1. 若$\mathbf{y}=[y_1,y_2,\ldots,y_m]^T,
A=\begin{bmatrix}
a_{11} & \cdots  & a_{1m}\\
\vdots & \ddots \vdots \\
a_{m1} & \cdots & a_{mm}
\end{bmatrix}_{m×m}
$,则$
\frac{\partial Ay}{\partial y} = A^T
$

    - 以二维矩阵为例，$\mathbf{y}=[y_1,y_2,\ldots,y_m]^T,A=\begin{bmatrix}
        a_{11} &  a_{12}\\
        a_{21} &  a_{22}
        \end{bmatrix}
        $

    - $$Ay=\begin{bmatrix}
        a_{11} &  a_{12}\\
        a_{21} &  a_{22}
        \end{bmatrix}
        \begin{bmatrix}
        y_1 \\
        y_2
        \end{bmatrix}=
        \begin{bmatrix}
        \frac{\partial a_{11}y_1+a_{12}y_2}{\partial y_2}  & \frac{\partial a_{21}y_1+a_{22}y_2}{\partial y_1} \\
        \frac{\partial a_{11}y_1+a_{12}y_2}{\partial y_2}  & \frac{\partial a_{21}y_1+a_{22}y_2}{\partial y_2} 
        \end{bmatrix}=
        \begin{bmatrix}
        a_{11} & a_{21}\\
        a_{12} & a_{22}
        \end{bmatrix}=A^T
        $$


2. 若$\mathbf{y}=[y_1,y_2,\ldots,y_m]^T,
A=\begin{bmatrix}
a_{11} & \cdots  & a_{1m}\\
\vdots & \ddots \vdots \\
a_{m1} & \cdots & a_{mm}
\end{bmatrix}_{m×m}
$,则$
\frac{\partial y^TAy}{\partial y} = Ay+A^Ty,当A对称时=2Ay
$

    - $\mathbf{y}=[y_1,y_2,\ldots,y_m]^T$
    - $ A=\begin{bmatrix}
        a_{11} &  a_{12}\\
        a_{21} &  a_{22}
        \end{bmatrix}
      $
    - $y^TAy=[y_1  y_2]
    \begin{bmatrix}
    a_{11}y_1+a_{12}y_2  \\
    a_{21}y_1+a_{22}y_2
    \end{bmatrix}=
    y_1(a_{11}y_1+a_{12}y_2)+y_2(a_{21}y_1+a_{22}y_2)
    $

    - $$\frac{\partial y^TAy}{\partial y}=
        \begin{bmatrix}
        \frac{\partial y^TAy}{\partial y_1} \\
        \frac{\partial y^TAy}{\partial y_2} \\
        \end{bmatrix}=
        \begin{bmatrix}
         a_{11}y_1+a_{11}y_1+a_{12}y_2+a_{21}y_2\\
         a_{12}y_1+a_{21}y_1+a_{22}y_2+a_{22}y_2\\
        \end{bmatrix}=
        \begin{bmatrix}
         a_{11}y_1+a_{21}y_2\\
         a_{12}y_1+a_{22}y_2\\
        \end{bmatrix}+
        \begin{bmatrix}
         a_{11}y_1+a_{12}y_2\\
         a_{21}y_1+a_{22}y_2\\
        \end{bmatrix}
        $$
    

## 三、线性回归应用
- $y=w_0+w_1x$
- $RSS(w)=\begin{bmatrix}
    y_1-(w_0+w_1x_1) \\
    y_2-(w_0+w_1x_2) \\
    \vdots \\
    y_n-(w_0+w_1x_n)
    \end{bmatrix}=
    \sum_{1}^n[y_i-(w_0+w_ix_i)]^2
    $
- $argmaxRSS(w)=[\frac{\partial RSS}{\partial w_o},\frac{\partial RSS}{\partial w_1}]=0$
- $Y=XW=\begin{bmatrix}
    1 & x_1 \\
    1 & x_2 \\
    \vdots \\
     1 & x_n
    \end{bmatrix}
    \begin{bmatrix}
    w_0  \\
    w_1 \\
    \end{bmatrix}
    $
- $RSS(W)=[y-XW]^T[y-XW]=y^Ty-y^TXW-W^TX^Ty+W^TX^TXW = y^Ty-2y^TXW+W^TX^TXW$
    - $\frac{\partial RSS}{\partial w}=0-2y^TX+2X^TXW=0$
    - $W = (X^TX)^-1y^TX$

## 四、链式法则
### 4.1 变量对向量求导
- $J=F(y(u))$
- $\mathbf{y}=[y_1,y_2,\ldots,y_m]^T$
- $\mathbf{u}=[u_1,u_2,\ldots,u_n]^T$

### 4.2 案例
- $\mathbf{y}=[y_1(u),y_2(u)]^T$
- $\mathbf{u}=[u_1,u_2,u_3]^T$
- $$\frac{\partial J}{\partial u}=
    \begin{bmatrix}
    \frac{\partial J}{\partial u_1}  \\
    \frac{\partial J}{\partial u_2} \\
    \frac{\partial J}{\partial u_3}
    \end{bmatrix}=
    \begin{bmatrix}
    \frac{\partial J}{\partial y_1(u)}\frac{\partial y_1(u)}{\partial u_1} + 
    \frac{\partial J}{\partial y_2(u)}\frac{\partial y_2(u)}{\partial u_1} \\
    \frac{\partial J}{\partial y_1(u)}\frac{\partial y_1(u)}{\partial u_2} + 
    \frac{\partial J}{\partial y_2(u)}\frac{\partial y_2(u)}{\partial u_2} \\
    \frac{\partial J}{\partial y_1(u)}\frac{\partial y_1(u)}{\partial u_3} + 
    \frac{\partial J}{\partial y_2(u)}\frac{\partial y_2(u)}{\partial u_3}
    \end{bmatrix}=
    \begin{bmatrix}
    \frac{\partial y_1(u)}{\partial u_1} & 
    \frac{\partial y_2(u)}{\partial u_1} \\
    \frac{\partial y_1(u)}{\partial u_2} &
    \frac{\partial y_2(u)}{\partial u_2} \\
    \frac{\partial y_1(u)}{\partial u_3} & 
    \frac{\partial y_2(u)}{\partial u_3}
    \end{bmatrix}
    \begin{bmatrix}
    \frac{\partial J}{\partial y_1}  \\
    \frac{\partial J}{\partial y_2} \\
    \end{bmatrix}=
     \frac{\partial y(u)}{\partial u}
     \frac{\partial J}{\partial y}
    $$



