### 4.1 An Overview of Classification | 分类概览

- **Definition | 定义**: The process of predicting a **qualitative response | 定性响应** (categorical variable) for an observation.
- **Mechanism**: Many classifiers first predict the probability that the observation belongs to each category, effectively behaving like regression methods.
- **Examples**:
    - Emergency room diagnosis (Stroke, Drug overdose, Epileptic seizure).
    - Online banking fraud detection.
    - DNA mutation analysis.

### 4.2 Why Not Linear Regression? | 为什么不使用线性回归？

- **Ordering Problem**: Encoding a qualitative response with $>2$ levels as a numerical variable (e.g., $1, 2, 3$) implies a specific ordering and distance between classes that may not exist in reality.
- **Probability Range**: For binary responses, linear regression may produce estimates outside the interval, making them difficult to interpret as probabilities.
- **Consistency**: Classifications from linear regression for a binary response are mathematically equivalent to the results of **Linear Discriminant Analysis (LDA) | 线性判别分析**.

### 4.3 Logistic Regression | 逻辑回归

- **Concept**: Instead of modeling the response $Y$ directly, it models the probability $p(X) = Pr(Y=1|X)$.

#### 4.3.1 The Logistic Model | 逻辑模型

- **Logistic Function | 逻辑函数**: To ensure output remains between 0 and 1, the model uses: $$p(X) = \frac{e^{\beta_0 + \beta_1 X}}{1 + e^{\beta_0 + \beta_1 X}}$$.
- **Odds | 几率**: The ratio of the probability of success to the probability of failure: $$\frac{p(X)}{1-p(X)} = e^{\beta_0 + \beta_1 X}$$.
- **Logit | 对数几率**: The log-odds is linear in $X$: $$\log\left(\frac{p(X)}{1-p(X)}\right) = \beta_0 + \beta_1 X$$.

#### 4.3.2 Estimating the Regression Coefficients | 估计回归系数

- **Maximum Likelihood | 极大似然法**: The preferred method for estimating coefficients $\beta_0, \beta_1$ by maximizing the likelihood function: $$\ell(\beta_0, \beta_1) = \prod_{i:y_i=1} p(x_i) \prod_{i':y_{i'}=0} (1 - p(x_{i'}))$$.
- **Z-statistic**: Used to test the null hypothesis $H_0: \beta_1 = 0$; a large absolute value indicates an association between the predictor and the response.

#### 4.3.3 Making Predictions | 进行预测

- **Computation**: Once coefficients are estimated, probabilities can be calculated for any value of $X$.
- **Dummy Variables | 哑变量**: Qualitative predictors can be incorporated using $0/1$ encoding.

#### 4.3.4 Multiple Logistic Regression | 多元逻辑回归

- **Model**: Generalizes to $p$ predictors: $$\log\left(\frac{p(X)}{1-p(X)}\right) = \beta_0 + \beta_1 X_1 + \dots + \beta_p X_p$$.
- **Confounding | 混杂**: Results for a predictor in a simple model may differ or even reverse in a multiple model due to correlations between predictors (e.g., student status and credit balance).

#### 4.3.5 Multinomial Logistic Regression | 多元分类逻辑回归

- **Approach**: Extends to $K > 2$ classes by selecting a **baseline class | 基准类**.
- **Softmax Coding | Softmax 编码**: An alternative symmetric representation used in machine learning: $$Pr(Y=k|X=x) = \frac{e^{\beta_{k0} + \dots + \beta_{kp}x_p}}{\sum_{l=1}^K e^{\beta_{l0} + \dots + \beta_{lp}x_p}}$$.

### 4.4 Generative Models for Classification | 分类的生成模型

- **Mechanism**: Models the distribution of predictors $X$ separately in each class ($Pr(X|Y=k)$) and uses **Bayes' Theorem | 贝叶斯定理** to flip them into posterior probabilities.
- **Bayes' Theorem Formula**: $$Pr(Y=k|X=x) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)}$$.
    - $\pi_k$: **Prior probability | 先验概率**.
    - $f_k(x)$: **Density function | 密度函数**.

#### 4.4.1 Linear Discriminant Analysis for $p = 1$ | $p=1$ 时的线性判别分析

- **Assumptions**: $f_k(x)$ is **Normal (Gaussian) | 正态分布** and all classes share a common variance $\sigma^2$.
- **Discriminant Function | 判别函数**: Assign observation to class $k$ that maximizes: $$\delta_k(x) = x \cdot \frac{\mu_k}{\sigma^2} - \frac{\mu_k^2}{2\sigma^2} + \log(\pi_k)$$.

#### 4.4.2 Linear Discriminant Analysis for $p > 1$ | $p > 1$ 时的线性判别分析

- **Assumptions**: $X$ follows a **Multivariate Gaussian | 多元正态分布** with a class-specific mean vector $\mu_k$ and a shared covariance matrix $\Sigma$.
- **Confusion Matrix | 混杂矩阵**: Used to display correct classifications and different types of errors (false positives vs. false negatives).
- **Sensitivity and Specificity | 敏感性与特异性**: Performance measures for binary classifiers.
- **ROC Curve | ROC 曲线**: Displays the trade-off between the **True Positive Rate | 真阳性率** and **False Positive Rate | 假阳性率** across all thresholds.

#### 4.4.3 Quadratic Discriminant Analysis | 二次判别分析

- **Assumption**: Similar to LDA but each class has its own **covariance matrix | 协方差矩阵** $\Sigma_k$.
- **Nature**: Results in a **quadratic | 二次** function of $x$ for the discriminant rule.
- **Bias-Variance Trade-off**: QDA is more flexible (lower bias) than LDA but has higher variance; preferred when the shared covariance assumption is clearly violated.

#### 4.4.4 Naive Bayes | 朴素贝叶斯

- **Independence Assumption**: Assumes that within the $k$th class, the $p$ predictors are independent.
- **Effect**: Reduces a $p$-dimensional task to $p$ one-dimensional tasks, significantly reducing variance at the cost of some bias.

### 4.5 A Comparison of Classification Methods | 分类方法比较

#### 4.5.1 An Analytical Comparison | 解析比较

- **Log-odds**: For LDA, QDA, and Naive Bayes, the log-odds are respectively linear, quadratic, or additive functions of the predictors.
- **Logistic vs. LDA**: LDA outperforms when normality assumptions hold; Logistic regression is more robust when they do not.

#### 4.5.2 An Empirical Comparison | 实证比较

- No single method dominates; performance depends on the true decision boundary's shape and the data distribution.

### 4.6 Generalized Linear Models | 广义线性模型

- **Context**: Applicable when the response is neither qualitative nor quantitative, such as **counts | 计数**.

#### 4.6.1 Linear Regression on the Bikeshare Data | 在自行车共享数据上的线性回归

- **Issues**: Linear models can predict negative counts and fail to handle **heteroscedasticity | 异方差性** (variance increasing with the mean).

#### 4.6.2 Poisson Regression on the Bikeshare Data | 在自行车共享数据上的泊松回归

- **Poisson Distribution | 泊松分布**: Used for non-negative integer counts.
- **Model**: Models the log of the mean as a linear function: $\log(\lambda(X)) = \beta_0 + \beta_1 X_1 + \dots + \beta_p X_p$.

#### 4.6.3 Generalized Linear Models in Greater Generality | 更具普遍性的广义线性模型

- **Structure**: Consists of a distribution from the **exponential family | 指数族** and a **link function | 连接函数** $\eta$ that transforms the mean into a linear predictor.