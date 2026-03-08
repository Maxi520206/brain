#Reinforcement_Learning 
# [[B63C3-Finite Markov Decision Process]]
### 3.2 Goals and Rewards

- **Reward Signal | 奖励信号**: A simple number $R_t$ sent from the environment to the agent.
- **Goal**: To maximize the total amount of reward (cumulative reward) received over the long run.
- **The Reward Hypothesis**: "That all of what we mean by goals and purposes can be well thought of as the maximization of the expected value of the cumulative sum of a received scalar signal (called reward)".
- **Note**: The reward signal is the way of communicating _what_ the agent is to achieve, not _how_ it is to achieve it.

### 3.3 Returns

- **Expected Return | 期望回报 ($G_t$)**: The specific function of the reward sequence that the agent seeks to maximize.
- **Simple Sum (Episodic Tasks)**:
    - $G_t = R_{t+1} + R_{t+2} + R_{t+3} + \dots + R_T$.
    - Used in **Episodic Tasks | 回合制任务**, where interaction breaks into subsequences (episodes) ending in a terminal state.
- **Discounted Return | 折扣回报**:
    - $G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \dots = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}$.
    - **Discount Rate | 折扣率 ($\gamma$)**: $0 \le \gamma \le 1$. It determines the present value of future rewards.
    - If $\gamma < 1$ and the reward sequence is bounded, the infinite sum has a finite value.
### 3.4 Unified Notation for Episodic and Continuing Tasks

- **Continuing Tasks | 连续性任务**: Tasks where the agent–environment interaction does not break naturally into episodes but continues without limit.
- **Unification**: Episode termination is treated as entering a special **absorbing state** that transitions only to itself and generates zero rewards.
- **Unified Return Formula**:
    - $G_t = \sum_{k=0}^{T-t-1} \gamma^k R_{t+k+1}$.
    - Allows for the possibility that $T = \infty$ or $\gamma = 1$ (but not both).

### 3.5 The Markov Property

- **Definition**: A state signal that compactly summarizes the past without degrading the ability to predict the future.
- **Requirement**: The state $S_t$ should include all information about the history of sensations that make a difference to the future.
- **Causal Dynamics**: In a Markov state, the environment's response at $t+1$ depends only on the state and action at $t$.
- **Significance**: decisions and values are assumed to be a function only of the current state; all theory in the book assumes Markov state signals.

### 3.6 Markov Decision Processes

- **MDP | 马尔可夫决策过程**: A reinforcement learning task that satisfies the Markov property.
- **Finite MDP**: An MDP with finite state, action, and reward sets.
- **Dynamics Function**:
    - $p(s', r|s, a) \doteq \text{Pr}{S_{t+1} = s', R_{t+1} = r | S_t = s, A_t = a}$.
    - This function completely specifies the dynamics of a finite MDP.
- **Derived Equations**:
    - **State-transition probabilities**: $p(s'|s, a) = \sum_{r \in \mathcal{R}} p(s', r|s, a)$.
    - **Expected rewards for state–action pairs**: $r(s, a) = \sum_{r \in \mathcal{R}} r \sum_{s' \in \mathcal{S}} p(s', r|s, a)$.
- **Transition Graph**: A summary of MDP dynamics where large open circles are states and small solid circles are state–action pairs.

> [!NOTE] 如何理解Markov过程？
> 	MDP 包含 5 个元素：
> 	S — 状态 (State) 系统当前情况。
> 	A — 动作 (Action) Agent 可以做的选择：
> 	P — 状态转移概率p(s′,r∣s,a)在 **状态 s**  采取 **动作 a** 变成：下一个状态 **s'** 获得奖励 **r** 的概率。
> 	R — 奖励函数 奖励代表行为好坏。
> 	γ — 折扣因子 表示 **未来奖励的重要程度** 




# [[B20C1-Introduction to Probabilities, Graphs, and Causal Models#^1632d9]]
[[KB4.2-Causal Model]]
[[E15-Causal inference in statistics]]

### 1.4.2 Probabilistic Predictions in Causal Models

- **Causal Markov Condition | 因果马尔可夫条件**: Every Markovian causal model induces a distribution where each variable is independent of its nondescendants given its parents.
- **Common-Cause Assumption**: Dependence between any two variables implies one causes the other or a third variable causes both.
- **Judgmental Advantages**: Assumptions of conditional independence are easier to judge in functional models because they are cast as judgments about the presence or absence of unobserved common causes.
