
### 5.1 Cross-Validation | 交叉验证

- **Test Error vs. Training Error**:
    - **Test Error | 测试误差**: The average error resulting from predicting the response on a new observation not used in training.
    - **Training Error | 训练误差**: Calculated by applying the method to the observations used in its training; it often dramatically underestimates the test error.
- **Core Objective**: To estimate the test error rate using the available training data when a large designated test set is unavailable.

#### 5.1.1 The Validation Set Approach | 验证集方法

- **Definition**: A strategy involving randomly dividing the available observations into two parts: a **training set | 训练集** and a **validation set | 验证集** (or **hold-out set | 留出集**).
- **Mechanism**: The model is fit on the training set, and its performance (e.g., MSE) is evaluated on the validation set.
- **Drawbacks**:
    1. **High Variability | 高变异性**: The estimated test error rate can vary significantly depending on which observations are included in which set.
    2. **Overestimation of Test Error**: Since the model is trained on only a subset of data, it tends to perform worse than it would if trained on the entire dataset, leading to an upward bias in the test error estimate.

#### 5.1.2 Leave-One-Out Cross-Validation | 留一交叉验证

- **Definition | LOOCV**: A refinement of the validation set approach where the validation set consists of a single observation $(x_1, y_1)$, and the remaining $n-1$ observations make up the training set.
- **Procedure**: The process is repeated $n$ times, such that each observation is used as the validation set exactly once.
- **Estimate Formula**: The average of the $n$ resulting test error estimates: $$CV_{(n)} = \frac{1}{n} \sum_{i=1}^n MSE_i$$.
- **Advantages**:
    - Far less bias compared to the validation set approach because it uses $n-1$ observations for training.
    - Yields identical results every time (no randomness in splitting).
- **Computational Shortcut**: For least squares linear or polynomial regression, the cost of LOOCV is the same as a single model fit: $$CV_{(n)} = \frac{1}{n} \sum_{i=1}^n \left( \frac{y_i - \hat{y}_i}{1 - h_i} \right)^2$$ where $\hat{y}_i$ is the $i$th fitted value from the original fit and $h_i$ is the **leverage | 杠杆值**.

#### 5.1.3 $k$-Fold Cross-Validation | $k$ 折交叉验证

- **Definition**: Randomly dividing the set of observations into $k$ groups, or **folds | 折**, of approximately equal size.
- **Procedure**: One fold is treated as a validation set, and the model is fit on the remaining $k-1$ folds. This is repeated $k$ times.
- **Estimate Formula**: $$CV_{(k)} = \frac{1}{k} \sum_{i=1}^k MSE_i$$.
- **Common Values**: Typically $k=5$ or $k=10$ are used in practice.
- **Comparison to LOOCV**: $k$-fold CV is computationally more feasible for models with intensive fitting procedures or extremely large $n$.

#### 5.1.4 Bias-Variance Trade-Off for $k$-Fold Cross-Validation | $k$ 折交叉验证的偏差-方差权衡

- **Bias Reduction | 偏差减小**:
    - LOOCV has lower bias than $k$-fold CV (where $k < n$) because it uses a training set of size $n-1$, which is nearly the full dataset.
- **Variance Reduction | 方差减小**:
    - LOOCV often has higher variance than $k$-fold CV when $k < n$. This is because in LOOCV, we average the outputs of $n$ models that are trained on almost identical sets of observations, making their results highly positively correlated.
    - The mean of highly correlated quantities has higher variance than the mean of less correlated ones.
- **Conclusion**: $k=5$ or $k=10$ typically results in a test error rate estimate that suffers neither from excessively high bias nor very high variance.

#### 5.1.5 Cross-Validation on Classification Problems | 分类问题中的交叉验证

- **Metric**: Instead of MSE, CV uses the number of misclassified observations.
- **LOOCV Error Rate**: $$CV_{(n)} = \frac{1}{n} \sum_{i=1}^n Err_i$$ where $Err_i = I(y_i \neq \hat{y}_i)$.
- **Usage**: CV helps decide between models with different levels of flexibility (e.g., polynomial orders or $K$ in KNN) by finding the minimum point of the CV error curve.