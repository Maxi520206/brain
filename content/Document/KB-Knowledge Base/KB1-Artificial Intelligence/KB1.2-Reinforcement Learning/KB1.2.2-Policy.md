#Reinforcement_Learning #Machine_Learning 
# [[B63C3-Finite Markov Decision Process]]
**Policy | 策略 ($\pi_t$)**:
    - A mapping from states to probabilities of selecting each possible action.
    - $\pi_t(a|s)$: The probability that $A_t = a$ if $S_t = s$.
# [[B63C4-Dynamic Programming]]
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
