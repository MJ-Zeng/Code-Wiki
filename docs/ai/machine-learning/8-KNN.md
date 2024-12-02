# k-Nearest Neighbor (kNN)

## 1. Introduction

Overview

- kNN is the simplest supervised learning method, especially useful when prior knowledge on the data is very limited
- It allows simultaneous training and testing
- When classifying a test sample x, find the closest k samples in the training set; classify the test sample based on majority vote of labels in those samples
- Low bias, high variance

Advantages
- Not sensitive to outliers
- Easy to implement and parallelize
- Good for large training sets

Drawbacks
- Need to tune hyperparameter k
- Large storage requirements
- Computationally intensive


![](https://files.mdnice.com/user/75397/6a7810ef-b255-474b-a744-a756c92ffe29.png)


## 2.Algorithm: k-Nearest Neighbors (k-NN)

Input：
- Training set: $D_{train} = \{(x_1, y_1), \ldots, (x_N, y_N)\}$
- Test sample: $x$ without label $y$
- Hyperparameter: $k$
- Distance metric: $d(x, y)$

Output：
Predicted label $y_{pred}$ for $x$

Steps：
1. Compute $d(x, x_j)$ for each $(x_j, y_j) \in D_{train}$
2. Sort the distances in ascending order, choose the first $k$ samples $(x_(1), y(1)), \ldots, (x_k, y(k))$
3. - Classification: Make majority vote: $y_{pred} = Mode(y_1, \ldots, y_k)$
   - Regression: $y_{pred} = Average(y_1, \ldots, y_k)

## 3. Distance Metrics

1. Minkowski distance :
$$ 
d_h(\mathbf{x}_1, \mathbf{x}_2) = \left( \sum_{i=1}^{d} |x_{1i} - x_{2i}|^h \right)^{\frac{1}{h}} 
$$
    - h = 2, Euclidean distance,
    - h = 1, Manhattan distance


3. Mahalanobis distance :
$$
d(\mathbf{x}_1,\mathbf{x}_2)=\sqrt{(\mathbf{x}_1-\mathbf{x}_2)^T\Sigma^{-1}(\mathbf{x}_1-\mathbf{x}_2)}
$$
  where $\Sigma$ is the covariance matrix of sample set ; introduce correlations, could be applied to the non-scaling data

4. Hamming distance :
$$
Hamming(\mathbf{x}_1,\mathbf{x}_2)=d-\sum_{i=1}^{d}l(x_{1i}=x_{2i})
$$
    - used to compare two strings, e.g., 
    - $Hamming('toned', 'roses') = 3$, 
    - $Hamming('011101', '011101') = 2$

## 4. Tuning K

- Different values of k leads to different results
- Cross-validation to tune k


## 5. Example


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import pprint
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from collections import Counter


def distance(x,y,p=2):
    return np.power(np.sum(np.power(np.abs(x - y), p),1), 1 / p)

iris = load_iris()
df = pd.DataFrame(iris.data,columns=iris.feature_names)
df['label'] = iris.target
df.columns = ['sepal length', 'sepal width', 'petal length', 'petal width', 'label']

data = np.array(df.iloc[:100, [0, 1, -1]])
X, y = data[:,:-1], data[:,-1]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)


class KNNClassification:
    def __init__(self,X_train,y_train,n_neighbors=3,p=2):
        self.k=n_neighbors
        self.p=p
        self.X_train = X_train
        self.y_train = y_train

    def predict(self,X):
        diss = distance(self.X_train,X,self.p)
        diss_idx = np.argsort(diss)
        top_k_idx = diss_idx[:self.k]
        top_k_diss = diss[top_k_idx]
        top_k_points = self.X_train[top_k_idx]
        top_k_y = self.y_train[top_k_idx]
        counter = Counter(top_k_y)
        label = counter.most_common(1)[0][0]
        return label,top_k_points,top_k_diss

    def score(self,X_test,y_test):
        right_count = 0
        for X,y in zip(X_test,y_test):
            label = self.predict(X)[0]
            if label == y:
                right_count+=1
        return right_count/len(X_test)


clf = KNNClassification(X_train, y_train) 
clf.score(X_test, y_test)
```




    0.95




```python
def find_best_k(X_train, y_train, X_val, y_val, k_values):
    best_k = None
    best_mse = float('inf')
    best_model = None
    
    for k in k_values:
        model = KNNClassification(X_train, y_train, n_neighbors=k, p=2)
        score = model.score(X_val, y_val)
        print(f"K={k}, score={mse:.4f}")
        
        if mse < best_mse:
            best_mse = mse
            best_k = k
            best_model = model
            
    return best_k, best_mse, best_model

X_train, X_val, y_train, y_val = train_test_split(X_train, y_train, test_size=0.25, random_state=42)

k_values = range(1, 11)

best_k, best_mse, best_model = find_best_k(X_train, y_train, X_val, y_val, k_values)
print(f"Best K={best_k}, Best score={best_mse:.5f}")

test_mse = best_model.score(X_test, y_test)
print(f"Test score with Best K={best_k}: {test_mse:.5f}")
```

    K=1, score=0.0222
    K=2, score=0.0222
    K=3, score=0.0222
    K=4, score=0.0222
    K=5, score=0.0222
    K=6, score=0.0222
    K=7, score=0.0222
    K=8, score=0.0222
    K=9, score=0.0222
    K=10, score=0.0222
    Best K=1, Best score=0.02222
    Test score with Best K=1: 1.00000
    


```python
class KNNRegressor:
    def __init__(self, X_train, y_train, n_neighbors=3, p=2):
        self.k = n_neighbors
        self.p = p
        self.X_train = X_train
        self.y_train = y_train

    def predict(self, X):
        diss = distance(self.X_train, X, self.p)
        diss_idx = np.argsort(diss)
        top_k_idx = diss_idx[:self.k]
        top_k_y = self.y_train[top_k_idx]
        label = np.mean(top_k_y)
        return label

    def score(self, X_test, y_test):
        predictions = np.array([self.predict(X) for X in X_test])
        mse = np.mean((predictions - y_test) ** 2)
        return mse
        
clf = KNNRegressor(X_train, y_train, n_neighbors=3, p=2)
mse = clf.score(X_test, y_test)
print(f"Mean Squared Error: {mse:.2f}")
```

    Mean Squared Error: 0.02
    


```python
def find_best_k(X_train, y_train, X_val, y_val, k_values):
    best_k = None
    best_mse = float('inf')
    best_model = None
    
    for k in k_values:
        model = KNNRegressor(X_train, y_train, n_neighbors=k, p=2)
        mse = model.score(X_val, y_val)
        print(f"K={k}, MSE={mse:.4f}")
        
        if mse < best_mse:
            best_mse = mse
            best_k = k
            best_model = model
            
    return best_k, best_mse, best_model

X_train, X_val, y_train, y_val = train_test_split(X_train, y_train, test_size=0.25, random_state=42)

k_values = range(1, 11)

best_k, best_mse, best_model = find_best_k(X_train, y_train, X_val, y_val, k_values)
print(f"Best K={best_k}, Best MSE={best_mse:.5f}")

test_mse = best_model.score(X_test, y_test)
print(f"Test MSE with Best K={best_k}: {test_mse:.5f}")
```

    K=1, MSE=0.0000
    K=2, MSE=0.0000
    K=3, MSE=0.0000
    K=4, MSE=0.0000
    K=5, MSE=0.0000
    K=6, MSE=0.0000
    K=7, MSE=0.0014
    K=8, MSE=0.0042
    K=9, MSE=0.0033
    K=10, MSE=0.0067
    Best K=1, Best MSE=0.00000
    Test MSE with Best K=1: 0.05000
    
