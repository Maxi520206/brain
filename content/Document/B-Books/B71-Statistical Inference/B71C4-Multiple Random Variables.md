#### 4.1 Joint and Marginal Distributions | 联合分布与边缘分布

- **Random Vector | 随机向量**: An $n$-dimensional random vector is a function from a sample space $S$ into $\mathbb{R}^n$.
- **Discrete Random Vectors | 离散随机向量**:
    - **Joint PMF | 联合概率质量函数**: $f(x,y) = P(X=x, Y=y)$.
    - **Calculation of Probabilities**: $P((X,Y) \in A) = \sum_{(x,y) \in A} f(x,y)$.
    - **Expectation**: $E g(X,Y) = \sum_x \sum_y g(x,y)f(x,y)$.
- **Marginal PMF | 边缘概率质量函数**:
    - $f_X(x) = \sum_{y \in \mathbb{R}} f_{X,Y}(x,y)$ and $f_Y(y) = \sum_{x \in \mathbb{R}} f_{X,Y}(x,y)$.
    - **Note**: Marginal distributions do not uniquely determine the joint distribution.
- **Continuous Random Vectors | 连续随机向量**:
    - **Joint PDF | 联合概率密度函数**: A function $f(x,y)$ such that $P((X,Y) \in A) = \iint_A f(x,y) dx dy$.
    - **Marginal PDF | 边缘概率密度函数**: $f_X(x) = \int_{-\infty}^{\infty} f(x,y) dy$.
- **Joint CDF | 联合累积分布函数**: $F(x,y) = P(X \le x, Y \le y)$.
    - **Relation to PDF**: $f(x,y) = \frac{\partial^2 F(x,y)}{\partial x \partial y}$ at continuity points.

#### 4.2 Conditional Distributions and Independence | 条件分布与独立性

- **Conditional PMF/PDF | 条件分布**:
    - $f(y|x) = \frac{f(x,y)}{f_X(x)}$ for $x$ such that $f_X(x) > 0$.
    - **Conditional Expectation**: $E(g(Y)|x) = \int g(y)f(y|x) dy$.
    - **Key Insight**: $E(g(Y)|X)$ is a **random variable** whose value depends on $X$.
- **Independence | 独立性**:
    - $X$ and $Y$ are independent if $f(x,y) = f_X(x)f_Y(y)$ for all $(x,y)$.
    - **Factorization Lemma | 分解引理**: $X$ and $Y$ are independent iff $f(x,y) = g(x)h(y)$ for some functions $g$ and $h$.
    - **Support Condition**: If $X$ and $Y$ are independent, the support of their joint density must be a cross-product set.
- **Properties of Independent r.v.s**:
    - $E(g(X)h(Y)) = (Eg(X))(Eh(Y))$.
    - **MGF of Sum**: $M_{X+Y}(t) = M_X(t)M_Y(t)$.
    - **Sum of Normals**: If $X \sim n(\mu, \sigma^2)$ and $Y \sim n(\gamma, \tau^2)$ are independent, $X+Y \sim n(\mu+\gamma, \sigma^2+\tau^2)$.

#### 4.3 Bivariate Transformations | 二元变量变换

- **Discrete Case**: $f_{U,V}(u,v) = \sum_{(x,y) \in A_{uv}} f_{X,Y}(x,y)$.
- **Continuous Case (One-to-one)**:
    - Let $x = h_1(u,v)$ and $y = h_2(u,v)$ be the inverse transformation.
    - $f_{U,V}(u,v) = f_{X,Y}(h_1(u,v), h_2(u,v)) |J|$.
    - **Jacobian | 雅可比行列式**: $J = \det \begin{pmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{pmatrix}$.

#### 4.4 Hierarchical Models and Mixture Distributions | 分层模型与混合分布

- **Hierarchical Model | 分层模型**: Describing a complex distribution through a sequence of simpler conditional models.
- **Law of Total Expectation | 全期望公式**: $EX = E(E(X|Y))$.
- **Law of Total Variance | 全方差公式**: $Var X = E(Var(X|Y)) + Var(E(X|Y))$.
    - $E(Var(X|Y))$ is the "within-group" variation.
    - $Var(E(X|Y))$ is the "between-group" variation.

#### 4.5 Covariance and Correlation | 协方差与相关系数

- **Covariance | 协方差**: $Cov(X,Y) = E((X-\mu_X)(Y-\mu_Y)) = EXY - \mu_X\mu_Y$.
- **Correlation | 相关系数**: $\rho_{XY} = \frac{Cov(X,Y)}{\sigma_X \sigma_Y}$.
- **Properties**:
    - Independence $\Rightarrow Cov(X,Y) = 0$, but uncorrelatedness does **not** imply independence.
    - $-1 \le \rho_{XY} \le 1$.
    - $|\rho_{XY}| = 1$ iff $P(Y = aX+b) = 1$ for some $a \ne 0$.
- **Variance of a Sum**: $Var(aX+bY) = a^2 Var X + b^2 Var Y + 2ab Cov(X,Y)$.
- **Bivariate Normal Distribution | 二元正态分布**:
    - Characterized by 5 parameters: $\mu_X, \mu_Y, \sigma_X^2, \sigma_Y^2, \rho$.
    - Conditional distribution $Y|X=x$ is normal with mean $\mu_Y + \rho\frac{\sigma_Y}{\sigma_X}(x-\mu_X)$ and variance $\sigma_Y^2(1-\rho^2)$.

#### 4.6 Multivariate Distributions | 多维分布

- **Multinomial Distribution | 多项分布**:
    - $P(X_1=x_1, \dots, X_n=x_n) = \frac{m!}{x_1! \dots x_n!} p_1^{x_1} \dots p_n^{x_n}$.
    - Marginal distribution of $X_i$ is $Binomial(m, p_i)$.
- **Mutual Independence | 相互独立**: $f(x_1, \dots, x_n) = \prod_{i=1}^n f_{X_i}(x_i)$.
- **Sums of r.v.s**:
    - Independent Gammas (same scale $\beta$): $\sum X_i \sim Gamma(\sum \alpha_i, \beta)$.
    - Linear combination of independent Normals is Normal.

#### 4.7 Inequalities | 不等式

##### 4.7.1 Numerical Inequalities | 数值不等式

- **Hölder’s Inequality | Hölder 不等式**: $E|XY| \le (E|X|^p)^{1/p} (E|Y|^q)^{1/q}$ where $\frac{1}{p} + \frac{1}{q} = 1$.
- **Cauchy–Schwarz Inequality | Cauchy-Schwarz 不等式**: $E|XY| \le (EX^2)^{1/2} (EY^2)^{1/2}$.
- **Liapounov’s Inequality | Liapounov 不等式**: $(E|X|^r)^{1/r} \le (E|X|^s)^{1/s}$ for $1 < r < s$.
- **Minkowski’s Inequality | Minkowski 不等式**: $[E|X+Y|^p]^{1/p} \le [E|X|^p]^{1/p} + [E|Y|^p]^{1/p}$.

##### 4.7.2 Functional Inequalities | 函数不等式

- **Jensen’s Inequality | Jensen 不等式**: If $g(x)$ is convex, $Eg(X) \ge g(EX)$.
- **Covariance Inequality | 协方差不等式**: If $g$ and $h$ are both nondecreasing, $E(g(X)h(X)) \ge (Eg(X))(Eh(X))$.