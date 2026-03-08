# [[B70C1-Probability and Counting]]
- **Sample Space $S$**: The set of all possible outcomes of an experiment.
- **Outcome $s$**: A single possible result of an experiment, visualized as a "pebble".
- **Event $A$** : A subset of the sample space $A \subseteq S$. An event occurred if the actual outcome is an element of that subset.
- **Definition of Probability**: Let $A$ be an event for an experiment with a finite sample space $S$ . The naive probability of $A$ is: $P_{naive}(A) = \frac{|A|}{|S|} = \frac{\text{number of outcomes favorable to } A}{\text{total number of outcomes in } S}$ .
- **Binomial coefficient**
    - **Definition**: Denoted as $\binom{n}{k}$ , read as "n choose k". It is the number of subsets of size $k$ for a set of size $n$ .
    - **Formula**: $\binom{n}{k} = \frac{n(n-1)\dots(n-k+1)}{k!} = \frac{n!}{k!(n-k)!}$ .
- **Axioms of Probability**
    
    1. $P(\emptyset) = 0 , P(S) = 1$ .
    2. **Countable Additivity**: If $A_1, A_2, \dots$ are disjoint events, then $P(\cup_{j=1}^\infty A_j) = \sum_{j=1}^\infty P(A_j)$ .
    
    - **Derived Properties**:
        - $P(A^c) = 1 - P(A)$ .
        - **Inclusion-Exclusion**: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ .
        - General Inclusion-Exclusion for $n$ events involves alternating sums of probabilities of all possible intersections.