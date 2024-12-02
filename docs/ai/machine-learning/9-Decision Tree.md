# Decision Tree

## 1.Introduction
- As an example, let’s imagine that you were trying to assess whether or not you should go surf, you may use the following decision rules to make a choice:

![](https://files.mdnice.com/user/75397/0d72f859-73c8-4213-b65f-cbbc312fd1c6.png)




## 2. How to choose features and split points?

- Impurity
Choose the feature and splitting point so that after each split the impurity should decrease the most.

- Example Comparison
If Impurity(M0) - Impurity(M12) > Impurity(M0) - Impurity(M34), choose A as the split node;
Otherwise, choose B.

![](https://files.mdnice.com/user/75397/43432b86-2b0a-4166-ad1f-4e39b74c7d41.png)


## 3.Types of Decision Trees
### 3.1 ID3 Algorithm
- Entropy at t: $$H(t)=-\sum_{c=1}^{C}p(c|t)\log_{2}{p(c|t)}$$
- Maximum at $\log_{2}{C}$,when $p(c|t)=\frac{1}{C}$
- Minimum at 0,when when $p(c|t)=1$
- Information gain:$$InfoGain_{split} = H(t) - \sum_{k=1}^{K}\frac{n_k}{n}H(K)$$ where $n_k$ is the number of samples in  the child node k,$n= \sum_{k=1}^{K}n_k$
- Drawback:easy to generate too many child nodes and overfit


### 3.2 C4.5 Algorithm
- Introduce information gain ratio:
  $$SplitINFO=-\sum_{k=1}^{K}\frac{n_k}{n}\log_{2}{\frac{n_k}{n}}$$
  $$InfoGainRatio = \frac{InfoGain_{split}}{SplitINFO}$$

### 3.3 CART 4.5
- Gini index of node t:$$Gini(t)=1-\sum_{c=1}^{C}(p(c|t))^2$$ where $p(c|t)$ is the proporation of class-c data in node t
- Maximum at $1-\frac{1}{C}$,when $p(c|t)=\frac{1}{C}$
- Minimum at 0,when when $p(c|t)=1$
- Gini index of split:$Gini_{split}=\sum_{k=1}^{K}\frac{n_k}{n}Gini(k)$ where $n_k$ is the number of samples in the child node k,$n= \sum_{k=1}^{K}n_k$
- Choose the split so that Gini(t) - $Gini_{split}$ is maximized

###  3.4 Misclassification Error
- Misclassification error at t:$$Error(t) = 1 - max_{c}{p(c|t)}$$
- Maximum at $1-\frac{1}{C}$,when $p(c|t)=\frac{1}{C}$
- Minimum at 0,when when $p(c|t)=1$


![](https://files.mdnice.com/user/75397/a21fa8d6-0eab-434d-96d8-af59d2f6d1d7.png)


## 4. Comparing Three Impurity Measures
- Consider a two-class problem with 400 observations in each class, (400, 400) ;two opossible splits,
  - A : (300, 100) + (100,300)
  - B : (200, 400) + (200, 0)

- $ \text{Gini}(A1) = 1 - \left( \frac{300}{400} \right)^2 - \left( \frac{100}{400} \right)^2 = 1 - \left( \frac{9}{16} \right) - \left( \frac{1}{16} \right) = 1 - \frac{10}{16} = \frac{6}{16} = \frac{3}{8} $
- $ \text{Gini}(A2) = 1 - \left( \frac{100}{400} \right)^2 - \left( \frac{300}{400} \right)^2 = 1 - \left( \frac{1}{16} \right) - \left( \frac{9}{16} \right) = 1 - \frac{10}{16} = \frac{6}{16} = \frac{3}{8} $
- $ \text{Gini}(A) = \frac{1}{2} \text{Gini}(A1) + \frac{1}{2} \text{Gini}(A2) = \frac{1}{2} \times \frac{3}{8} + \frac{1}{2} \times \frac{3}{8} = \frac{3}{8} $

- $ \text{Gini}(B1) = 1 - \left( \frac{200}{600} \right)^2 - \left( \frac{400}{600} \right)^2 = 1 - \left( \frac{1}{9} \right) - \left( \frac{4}{9} \right) = 1 - \frac{5}{9} = \frac{4}{9} $
- $ \text{Gini}(B2) = 1 - \left( \frac{200}{200} \right)^2 - \left( \frac{0}{200} \right)^2 = 1 - 1^2 - 0^2 = 0 $
- $ \text{Gini}(B) = \frac{3}{4} \text{Gini}(B1) + \frac{1}{4} \text{Gini}(B2) = \frac{3}{4} \times \frac{4}{9} + \frac{1}{4} \times 0 = \frac{1}{3} $


- $ H(A1) = -\frac{300}{400} \log_2 \frac{300}{400} - \frac{100}{400} \log_2 \frac{100}{400} = -\frac{3}{4} \log_2 \frac{3}{4} - \frac{1}{4} \log_2 \frac{1}{4} $
- $ H(A2) = -\frac{100}{400} \log_2 \frac{100}{400} - \frac{300}{400} \log_2 \frac{300}{400} = -\frac{1}{4} \log_2 \frac{1}{4} - \frac{3}{4} \log_2 \frac{3}{4} $
- $ H(A) = \frac{1}{2} H(A1) + \frac{1}{2} H(A2) = \frac{1}{2} \times \left( -\frac{3}{4} \log_2 \frac{3}{4} - \frac{1}{4} \log_2 \frac{1}{4} \right) + \frac{1}{2} \times \left( -\frac{1}{4} \log_2 \frac{1}{4} - \frac{3}{4} \log_2 \frac{3}{4} \right) \approx 0.81 $

- $ H(B1) = -\frac{200}{600} \log_2 \frac{200}{600} - \frac{400}{600} \log_2 \frac{400}{600} = -\frac{1}{3} \log_2 \frac{1}{3} - \frac{2}{3} \log_2 \frac{2}{3} $
- $ H(B2) = -\frac{200}{200} \log_2 \frac{200}{200} - \frac{0}{200} \log_2 \frac{0}{200} = 0 $
- $ H(B) = \frac{3}{4} H(B1) + \frac{1}{4} H(B2) = \frac{3}{4} \times \left( -\frac{1}{3} \log_2 \frac{1}{3} - \frac{2}{3} \log_2 \frac{2}{3} \right) + \frac{1}{4} \times 0 \approx 0.69 $

- $ \text{Error}(A1) = 1 - \max\left( \frac{300}{400}, \frac{100}{400} \right) = 1 - \frac{3}{4} = \frac{1}{4} $

- $ \text{Error}(A2) = 1 - \max\left( \frac{100}{400}, \frac{300}{400} \right) = 1 - \frac{3}{4} = \frac{1}{4} $

- $ \text{Error}(A) = \frac{1}{2} \text{Error}(A1) + \frac{1}{2} \text{Error}(A2) = \frac{1}{2} \times \frac{1}{4} + \frac{1}{2} \times \frac{1}{4} = \frac{1}{4} $



- $ \text{Error}(B1) = 1 - \max\left( \frac{200}{600}, \frac{400}{600} \right) = 1 - \frac{2}{3} = \frac{1}{3} $

- $ \text{Error}(B2) = 1 - \max\left( \frac{200}{200}, \frac{0}{200} \right) = 1 - 1 = 0 $

- $ \text{Error}(B) = \frac{3}{4} \text{Error}(B1) + \frac{1}{4} \text{Error}(B2) = \frac{3}{4} \times \frac{1}{3} + \frac{1}{4} \times 0 = \frac{1}{4} $

## 5. Tree Pruning
- Too complex tree structure easily leadss to overfitting
- Prepruning:set threshold $\delta$ for impurity decrease in splitting a node;if $\Delta Impurity_{split}>\delta$,do sliting,otherwise stop.
- Postpruning:based on cost function
$$Cost_{\alpha} = \sum_{t=1}^{|T|}n_t Impurity(t)+\alpha|T|$$

## 6.Pros and Cons
1. Advantages
    - Easy to interpret and visualize:widely used in finance,medical health,biology,etc
    - Easy to deal with missing values (treat as new data type)
    - Could be extended to regression
2. Drawbacks:
    - Easy to be trapped at local minimum because of greedy algorithm
    - Simple decision boundary:parallel lines to the axes

## 7.Exercise
## 7.1 Impurity Compute


```python
import numpy as np
import pandas as pd 
import matplotlib.pyplot as plt

from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

from collections import Counter
import math
from math import log

import pprint
```


```python
def create_data():
    datasets = [['青年', '否', '否', '一般', '否'],
               ['青年', '否', '否', '好', '否'],
               ['青年', '是', '否', '好', '是'],
               ['青年', '是', '是', '一般', '是'],
               ['青年', '否', '否', '一般', '否'],
               ['中年', '否', '否', '一般', '否'],
               ['中年', '否', '否', '好', '否'],
               ['中年', '是', '是', '好', '是'],
               ['中年', '否', '是', '非常好', '是'],
               ['中年', '否', '是', '非常好', '是'],
               ['老年', '否', '是', '非常好', '是'],
               ['老年', '否', '是', '好', '是'],
               ['老年', '是', '否', '好', '是'],
               ['老年', '是', '否', '非常好', '是'],
               ['老年', '否', '否', '一般', '否'],
               ]
    labels = [u'年龄',u'有工作',u'有自己的房子',u'信贷情况',u'类别']
    return datasets,labels

datasets,labels=create_data()
train_data = pd.DataFrame(datasets,columns=labels)
train_data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>年龄</th>
      <th>有工作</th>
      <th>有自己的房子</th>
      <th>信贷情况</th>
      <th>类别</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>青年</td>
      <td>否</td>
      <td>否</td>
      <td>一般</td>
      <td>否</td>
    </tr>
    <tr>
      <th>1</th>
      <td>青年</td>
      <td>否</td>
      <td>否</td>
      <td>好</td>
      <td>否</td>
    </tr>
    <tr>
      <th>2</th>
      <td>青年</td>
      <td>是</td>
      <td>否</td>
      <td>好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>3</th>
      <td>青年</td>
      <td>是</td>
      <td>是</td>
      <td>一般</td>
      <td>是</td>
    </tr>
    <tr>
      <th>4</th>
      <td>青年</td>
      <td>否</td>
      <td>否</td>
      <td>一般</td>
      <td>否</td>
    </tr>
    <tr>
      <th>5</th>
      <td>中年</td>
      <td>否</td>
      <td>否</td>
      <td>一般</td>
      <td>否</td>
    </tr>
    <tr>
      <th>6</th>
      <td>中年</td>
      <td>否</td>
      <td>否</td>
      <td>好</td>
      <td>否</td>
    </tr>
    <tr>
      <th>7</th>
      <td>中年</td>
      <td>是</td>
      <td>是</td>
      <td>好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>8</th>
      <td>中年</td>
      <td>否</td>
      <td>是</td>
      <td>非常好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>9</th>
      <td>中年</td>
      <td>否</td>
      <td>是</td>
      <td>非常好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>10</th>
      <td>老年</td>
      <td>否</td>
      <td>是</td>
      <td>非常好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>11</th>
      <td>老年</td>
      <td>否</td>
      <td>是</td>
      <td>好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>12</th>
      <td>老年</td>
      <td>是</td>
      <td>否</td>
      <td>好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>13</th>
      <td>老年</td>
      <td>是</td>
      <td>否</td>
      <td>非常好</td>
      <td>是</td>
    </tr>
    <tr>
      <th>14</th>
      <td>老年</td>
      <td>否</td>
      <td>否</td>
      <td>一般</td>
      <td>否</td>
    </tr>
  </tbody>
</table>
</div>




```python
d={'青年':1,'中年':2,'老年':3,'一般':1,'好':2,'非常好':3,'是':0,'否':1}
data = []
for i in range(15):
    tmp = []
    t = datasets[i]
    for tt in t:
       tmp.append(d[tt])
    data.append(tmp)
data = np.array(data)
data
```




    array([[1, 1, 1, 1, 1],
           [1, 1, 1, 2, 1],
           [1, 0, 1, 2, 0],
           [1, 0, 0, 1, 0],
           [1, 1, 1, 1, 1],
           [2, 1, 1, 1, 1],
           [2, 1, 1, 2, 1],
           [2, 0, 0, 2, 0],
           [2, 1, 0, 3, 0],
           [2, 1, 0, 3, 0],
           [3, 1, 0, 3, 0],
           [3, 1, 0, 2, 0],
           [3, 0, 1, 2, 0],
           [3, 0, 1, 3, 0],
           [3, 1, 1, 1, 1]])




```python
X,y=data[:,:-1],data[:,-1]
X.shape
```




    (15, 4)




```python


# 熵
def entropy(y):
    N = len(y)
    if N == 0:
        return 0  # 防止除以零的情况
    
    # 计算每个类别的计数
    counts = [np.sum(y == val) for val in set(y)]
    counts = np.array(counts)
    
    # 计算每个类别的概率
    p = counts / N
    
    # 计算熵
    entro = -np.sum(p * np.log2(p + 1e-10))  # 加一个小常数防止 log(0) 导致的 NaN
    return entro

# 条件熵
def cond_entropy(X,y,cond):
    N = len(y)
    cond_X = X[:,cond]
    tmp_entro = []
    for val in set(cond_X):
        tmp_y = y[cond_X == val]
        weight = len(tmp_y) / N
        tmp_entro.append(weight*entropy(tmp_y))
    return np.sum(tmp_entro)

# 信息增益
def info_gain(X,y,cond):
    return entropy(y) - cond_entropy(X,y,cond)

# 信息增益比
def info_gain_ratio(X,y,cond):
    return (entropy(y)-cond_entropy(X,y,cond))/cond_entropy(X,y,cond)

# gini系数
def gini(y):
    N = len(y)
    if N == 0:
        return 0    
    counts = [np.sum(y == val) for val in set(y)]
    counts = np.array(counts)    
    p = counts / N
    gini_t = 1 - sum(p**2)
    return  gini_t

def gini_split(X,y,cond):
    N = len(y)
    if N == 0:
        return 0  # 防止除以零的情况
    
    cond_X = X[:, cond]
    unique_vals = set(cond_X)
    gini_k = []
    
    for val in unique_vals:
        tmp_y = y[cond_X == val]
        weight = len(tmp_y) / N
        gini_k.append(weight * gini(tmp_y))
    
    gini_split_val = np.sum(gini_k)
    return gini_split_val

def gini_gain(X,y,cond):
    return gini(y)-gini_split(X,y,cond)

# def gini_gain(X,y,cond):
#     return gini(y)-gini_split(X,y,cond)
```


```python
entropy(y)
```




    0.9709505941661296




```python
# 年龄
cond_entropy(X,y,0)
```




    0.8879430943103608




```python
for i in range(4):
    print(f'{i} |info gain|info gain ratio| gini_gain |')
    print(f'   {info_gain(X,y,i):6.2f} , {info_gain_ratio(X,y,i):9.2f}  , {gini_gain(X,y,i):10.2f} ')    
```

    0 |info gain|info gain ratio| gini_gain |
         0.08 ,      0.09  ,       0.05 
    1 |info gain|info gain ratio| gini_gain |
         0.32 ,      0.50  ,       0.16 
    2 |info gain|info gain ratio| gini_gain |
         0.42 ,      0.76  ,       0.21 
    3 |info gain|info gain ratio| gini_gain |
         0.36 ,      0.60  ,       0.20 
    


```python
# get best feature

def best_split(X,y,method='info_gain'):
    _,M = X.shape
    if method == 'info_gain':
        split = info_gain
    elif method == 'info_gain_ratio':
        split = info_gain_ratio
    else:
        print('No such method')
    tmp_lst = []
    for i in range(M):
        tmp_lst.append(split(X,y,i))  
        
    #Returns the indices of the maximum values along an axis.
    best_feature = np.argmax(tmp_lst) 
    return best_feature


```


```python
best_split(X,y)
```




    2




```python
def majorityCnt(y):
    unique,count = np.unique(y,return_counts=True)
    return np.argmax(count)
majorityCnt(y)
```




    0



## 7.2 CART


```python
from sklearn.tree import DecisionTreeClassifier
from sklearn import tree

iris = load_iris()
X,y = iris.data,iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
clf = tree.DecisionTreeClassifier()
clf.fit(X_train,y_train)
print(clf.score(X_test,y_test))
plt.figure(figsize=(10, 8))
tree.plot_tree(clf, filled=True, feature_names=iris.feature_names, class_names=iris.target_names)
plt.show()
```

    0.9333333333333333
    


    

![](https://files.mdnice.com/user/75397/40232013-b4f7-464d-869c-898cfb88bffe.png)
    


## 8.Reference
- https://github.com/zhangzsustech/machinelearning
