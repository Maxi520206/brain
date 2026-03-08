

### 4.1 Policy Evaluation

- **Definition**: The process of computing the state-value function $v_\pi$ for an arbitrary policy $\pi$. This is also called the **prediction problem | 预测问题**.
- **Iterative Policy Evaluation | 迭代策略评估**:
    - Uses the Bellman equation for $v_\pi$ as an update rule.
    - **Assignment Rule**: $v_{k+1}(s) = \sum_{a} \pi(a|s) \sum_{s', r} p(s', r|s, a) [r + \gamma v_k(s')]$.
    - The sequence ${v_k}$ is guaranteed to converge to $v_\pi$ as $k \to \infty$ under technical conditions (e.g., $\gamma < 1$).
- **Full Backup | 全回溯**:
    - Updates are based on all possible next states (using the distribution model) rather than a single sample next state.
- **Implementation**:
    - **Synchronous**: Uses two arrays to keep old values fixed while computing new ones.
    - **In-place**: Uses one array, immediately overwriting old values. This usually converges faster because it uses new data as soon as it is available.

### 4.2 Policy Improvement

- **Objective**: To find a better policy using the value function of a current policy.
- **Policy Improvement Theorem | 策略改进定理**:
    - If for two deterministic policies $\pi$ and $\pi'$, $q_\pi(s, \pi'(s)) \ge v_\pi(s)$ for all $s \in \mathcal{S}$, then $\pi'$ is as good as or better than $\pi$ ($v_{\pi'}(s) \ge v_\pi(s)$).
- **Greedy Policy | 贪婪策略**:
    - A new policy $\pi'$ that is greedy with respect to the value function $v_\pi$ of the old policy $\pi$:
    - $\pi'(s) = \text{argmax}_a q_\pi(s, a) = \text{argmax}_a \sum_{s', r} p(s', r|s, a) [r + \gamma v_\pi(s')]$.
- **Optimality**: If the improved greedy policy $\pi'$ is no better than $\pi$, then both are optimal policies ($v_{\pi'} = v_*$).

### 4.3 Policy Iteration

- **Definition**: A sequence of alternating steps of policy evaluation and policy improvement to find an optimal policy.
- **Process**: $\pi_0 \xrightarrow{E} v_{\pi_0} \xrightarrow{I} \pi_1 \xrightarrow{E} v_{\pi_1} \xrightarrow{I} \pi_2 \xrightarrow{E} \dots \xrightarrow{I} \pi_* \xrightarrow{E} v_*$.
    - $\xrightarrow{E}$ denotes **Policy Evaluation | 策略评估**.
    - $\xrightarrow{I}$ denotes **Policy Improvement | 策略改进**.
- **Convergence**: For a finite MDP, it must converge to an optimal policy in a finite number of iterations.

### 4.4 Value Iteration

- **Motivation**: Policy iteration is slow because each iteration requires full policy evaluation (multiple sweeps).
- **Mechanism**: Truncates policy evaluation after just one sweep. It combines policy improvement and truncated evaluation into a single update.
- **Update Rule**: $v_{k+1}(s) = \max_a \sum_{s', r} p(s', r|s, a) [r + \gamma v_k(s')]$.
- **Note**: This is the Bellman optimality equation turned into an assignment statement.
- **Truncated Policy Iteration**: A class of algorithms that interposes multiple policy evaluation sweeps between each policy improvement sweep.

### 4.5 Asynchronous Dynamic Programming

- **Definition**: In-place iterative DP algorithms that are not organized in systematic sweeps of the entire state set.
- **Benefits**:
    - Avoids long sweeps over very large state spaces (the "curse of dimensionality").
    - Can focus backups on states that are most relevant to the agent's current experience.
- **Requirement**: To converge, the algorithm must continue to back up all states; no state can be ignored forever.

### 4.6 Generalized Policy Iteration

- **GPI | 广义策略迭代**: The general idea of letting policy evaluation and policy improvement processes interact, regardless of granularity.
- **Evaluation**: Makes the value function consistent with the current policy.
- **Improvement**: Makes the policy greedy with respect to the current value function.
- **Dynamics**: The two processes "compete" by pulling in opposing directions, but together they interact to find a single joint solution: the optimal values and policy.

### 4.7 Efficiency of Dynamic Programming

- **Computational Complexity**: DP methods find an optimal policy in time polynomial in the number of states and actions.
- **Comparison**: Polynomial time is exponentially faster than exhaustive search in the policy space.
- **Curse of Dimensionality | 维度灾难**: The difficulty where state sets grow exponentially with state variables. This is an inherent property of the problem, and DP handles it better than most competing methods.

### 4.8 Summary

- **Core Concepts**: Policy evaluation and policy improvement.
- **Popular Methods**: Policy iteration and value iteration.
- **Bootstrapping | 自举**: Updating estimates of values based on estimates of other values. This is a defining feature of DP and TD methods.
- **Context**: DP requires a perfect model of the environment and uses full backups.