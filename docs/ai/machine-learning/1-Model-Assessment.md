# Model Assessment 
## 一. Regression
### 1.1 Mean Square Error(MSE)
$$MSE=\frac{1}{n}\sum_{i=0}^{n}(y_i-\hat{y_i})$$



```python
import numpy as np
y_true = np.array([3, -0.5, 2, 7])
y_pred = np.array([2.5, 0.0, 2, 8])
mse=np.mean((y_true-y_pred)**2)
print(mse)

```

    0.375
    

### 1.2 Root Mean Square Error(RMSE)
$$RMSE=\sqrt{\frac{1}{n}\sum_{i=0}^{n}(y_i-\hat{y_i})^2}=\sqrt{MSE}$$


```python
import numpy as np
y_true = np.array([3, -0.5, 2, 7])
y_pred = np.array([2.5, 0.0, 2, 8])
rmse=np.sqrt(np.mean((y_true-y_pred)**2))
print(rmse)
```

    0.6123724356957945
    

### 1.3 Mean Absoulte Error(MAE)
$$MAE=\frac{1}{n}\sum_{i=0}^{n}| y_i-\hat{y_i} |$$


```python
import numpy as np
y_true = np.array([3, -0.5, 2, 7])
y_pred = np.array([2.5, 0.0, 2, 8])
mae=np.mean(np.abs(y_true,y_pred))
print(mae)
```

    3.125
    

### 1.4 Cofficient of Determination $R^2$
$$R^2 = 1-\frac{\sum_{i=0}^{n}(y_i-\hat{y_i})^2}{\sum_{i=0}^{n}(y_i-\bar{y_i})^2} $$ 

$R^2 \in [0,1]$:the larger of $R^2$,the smaller the ration of $SS_res$ to $SS_tot$,thus the betteer the model


```python
import numpy as np
y_true = np.array([3, -0.5, 2, 7])
y_pred = np.array([2.5, 0.0, 2, 8])
y_mean = np.mean(y_true)
sse = np.sum((y_true-y_pred)**2)
sst = np.sum((y_true-y_mean)**2)
r_square = 1.0-sse/sst
print(r_square)
```

    0.9486081370449679
    

### 1.5 Adjusted coefficient of determination 

• Adjusted coefficient of determination : $R^{2}_{\text{adj}} = 1 - \frac{(1-R^{2})(n-1)}{n-p-1}$  
• n is the number of samples, p is the dimensionality (or the number of attributes)  
• The larger the $R^{2}_{\text{adj}}$ value, the better performance the model  
• When adding important variables into the model, $R^{2}_{\text{adj}}$ gets larger and $SS_{\text{res}}$ is reduced  
• When adding unimportant variables into the model, $R^{2}_{\text{adj}}$ may get smaller and $SS_{\text{res}}$ may increase  
• In fact, one can show that $1 - R^{2}_{\text{adj}} = \frac{\sigma^{2}}{s^{2}}$, where  
  $s^{2} = \frac{1}{n-p-1} \sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^{2}$ and $S^{2} = \frac{1}{n-1} \sum_{i=1}^{n}(y_{i}-\bar{y})^{2}$ with  
  $E(s^{2}) = ES^{2} = \sigma^{2}$

  * 5.1 Prove $E(s^{2})  = \sigma^{2}$ *
$$\hat{\sigma^{2}}=\frac{SS_{\text{res}}}{n-p-1}$$
$$R^2=\frac{SS_{\text{res}}}{SS_{\text{tot}}}$$
$$1-R^{2}_{\text{adj}}=\frac{SS_{\text{res}}(n-1)}{SS_{\text{tot}}(n-p-1)}$$

$$1-R^{2}_{\text{adj}}=\frac{\hat{\sigma^{2}}(n-1)}{SS_{\text{tot}}}=\frac{\hat{\sigma^{2}}}{s^{2}}$$


```python
import numpy as np
y_true = np.array([3, -0.5, 2, 7])
y_pred = np.array([2.5, 0.0, 2, 8])
n = len(y_true)
for p in range(3):
    r_adjust = 1.0 - (1-r_square)*(n-1)/(n-p-1)
    print(p,r_adjust)
```

    0 0.9486081370449679
    1 0.9229122055674519
    2 0.8458244111349038
    

### 1.6 MSE/RMSE/MAE
| 指标 | 特性 | 优点 | 缺点 | 适用场景 |
|------|------|------|------|----------|
| MAE  | - 鲁棒性强 <br> - 解释直观 | - 减少异常值影响 <br> - 易于理解 | - 导数非平滑 <br> - 缺乏对大误差的敏感性 | - 异常值多的数据集 <br> - 需要直观误差度量的情况 |
| MSE  | - 平滑函数 <br> - 放大误差 | - 优化过程容易处理 <br> - 突出大误差 | - 对异常值敏感 <br> - 较难解释 | - 需要强调大误差的情况 <br> - 数据较干净 |
| RMSE | - 单位与数据一致 <br> - 常用标准 | - 直接与实际值比较 <br> - 区分度高 | - 对异常值敏感 <br> - 较难解释 | - 需要与实际值直接比较的情况 <br> - 数据较干净 |

## 二、Confusion Matrix

|                       |         Predicted Positive (+)         |         Predicted Negative (-)        |
|:---------------------:|:-------------------------------------:|:-------------------------------------:|
| **Actual Positive (+)** | **True Positive (TP)**                | **False Negative (FN)**              |
| **Actual Negative (-)** | **False Positive (FP)**               | **True Negative (TN)**               |

- **TP** = True positives: a positive label is correctly predicted
- **TN** = True negatives: a negative label is correctly predicted
- **FP** = False positives: a negative label is predicted as a positive
- **FN** = False negatives: a positive label is predicted as a negativeive

### 2.1 Accuracy
- Accuracy is the proportion of correct predictions among the total number of cases examined.
  $$Accuracy = \frac{TP+TN}{TP+FN+FP+TN}$$
- When the class distribution is relatively balanced, accuracy is a good evaluation metric.
- **Models that are unbiased but often give wrong answers**   
  
|               | Model Prediction (+) | Model Prediction (-) |
|---------------|----------------------|----------------------|
| **Actual (+)**| 250 (True Positive)  | 250 (False Negative) |
| **Actual (-)**| 250 (False Positive) | 250 (True Negative)  |

- **Biased data usually contains only one type of label**

|               | Model Prediction (+) | Model Prediction (-) |
|---------------|----------------------|----------------------|
| **Actual (+)**| 400 (True Positive)  | 100 (False Negative) |
| **Actual (-)**| 400 (False Positive) | 100 (True Negative)  |

- **Biased models typically generate a label**

|               | Model Prediction (+) | Model Prediction (-) |
|---------------|----------------------|----------------------|
| **Actual (+)**| 400 (True Positive)  | 400 (False Negative) |
| **Actual (-)**| 100 (False Positive) | 100 (True Negative)  |ve)  |ng)low)|</td>
  </tr>
</table>

### 2.2 Sensitivity/Recall

- *Sensitivity* and *Recall* are interchangeable names for the same metric, which expresses the fraction of samples __correctly__ predicted by a model:

$$sensitivity = recall = \frac{TP}{TP + FN}$$

- This is an important metric, that tells us how out of all the *actually* __positive__ samples, how many are __correctly__ predicted as positive.
- When the cost of misclassifying a positive class as a negative class is high (such as in disease detection),


### 2.3 Specificity
- Specificity expresses the fraction of __negative__ labels correctly predicted over the total number of existing negative samples:

$$specificity =  \frac{TN}{TP + FN}$$

- Specificity tells us how out of all the *actually* __negative__ samples, how many are __correctly__ predicted as negative.

### 2.4 Precision
- Precision expresses the proportion of __correctly__ predicted positive samples over all positive predictions:

$$precision = \frac{TP}{TP + FP}$$

- In other words, it indicates how out of all positive predictions, how many are truly positive labels.
- When the cost of misclassifying a negative class as a positive class is high (such as in spam email filtering), it is crucial to manage this risk appropriately.

### 2.5 F1 Score

- F1-Score 是精确率和召回率的调和平均，用于平衡两者之间的影响。
$$F1=\frac{(1+\beta^2)(Precision*recall)}{\beta^2Precision+recall}$$

- F1 Score是一个用于衡量二分类或多分类任务中模型性能的指标，尤其是在处理类别不平衡的数据集时非常有用

### 2.6 AUC-ROC

- The ROC curve stands for the Receiver Operating Characteristic curve

![](https://files.mdnice.com/user/75397/0ac38d21-5641-459f-b10f-d0854ca5cf39.png)


![](https://files.mdnice.com/user/75397/aefe4875-bdfb-4c2a-9566-67a760156cdd.png)


- ROC AUC stands for Receiver Operating Characteristic Area Under the Curve.

![](https://files.mdnice.com/user/75397/8023ffe7-03f2-41cb-b483-8a7f9484aabf.png)


- The better the model can distinguish between positive and negative classes, the closer the curve is to the top left corner of the graph.

![](https://files.mdnice.com/user/75397/9ce57e51-97d3-4531-ae8e-9683596dc8a2.png)


- As a rule of thumb, a ROC AUC score above 0.8 is considered good, while a score above 0.9 is considered great. 


```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import confusion_matrix, classification_report, roc_curve, auc, roc_auc_score

# 加载 Iris 数据集
iris = datasets.load_iris()
X = iris.data
y = iris.target

# 将多分类问题转换为多个二分类问题
n_classes = len(np.unique(y))
y_one_hot = np.eye(n_classes)[y]

# 划分数据集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# 创建分类器并训练
classifier = DecisionTreeClassifier(random_state=42,max_depth=2)
classifier.fit(X_train, y_train)

# 预测测试集
y_pred = classifier.predict(X_test)

# 计算混淆矩阵
cm = confusion_matrix(y_test, y_pred)
print("Confusion Matrix:")
print(cm)

# 计算分类报告（包括精确率、召回率、F1 Score）
report = classification_report(y_test, y_pred, target_names=iris.target_names)
print("\nClassification Report:")
print(report)

# 预测概率
y_score = classifier.predict_proba(X_test)

# 计算每个类别的ROC AUC
fpr = dict()
tpr = dict()
roc_auc = dict()

for i in range(n_classes):
    fpr[i], tpr[i], _ = roc_curve(y_test == i, y_score[:, i])
    roc_auc[i] = auc(fpr[i], tpr[i])

# 绘制ROC曲线
plt.figure()
colors = ['blue', 'red', 'green']
for i, color in zip(range(n_classes), colors):
    plt.plot(fpr[i], tpr[i], color=color, lw=2,
             label=f'ROC curve (area = {roc_auc[i]:.2f}) for class {iris.target_names[i]}')

plt.plot([0, 1], [0, 1], 'k--', lw=2)
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic for Iris Dataset')
plt.legend(loc="lower right")
plt.show()
```

    Confusion Matrix:
    [[19  0  0]
     [ 0 12  1]
     [ 0  0 13]]
    
    Classification Report:
                  precision    recall  f1-score   support
    
          setosa       1.00      1.00      1.00        19
      versicolor       1.00      0.92      0.96        13
       virginica       0.93      1.00      0.96        13
    
        accuracy                           0.98        45
       macro avg       0.98      0.97      0.97        45
    weighted avg       0.98      0.98      0.98        45
    
    

![](https://files.mdnice.com/user/75397/05b9ef59-424c-4cf7-a9b0-b0f5ebbe2f00.png)

    

