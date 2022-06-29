# RL-SequenceModels

### TT-Trajectory Transformer

**Paper** [Offline Reinforcement Learning as One Big Sequence Modeling Problem](https://proceedings.neurips.cc/paper/2021/file/099fe6b0b444c23836c4a5d07346082b-Paper.pdf)<br>
**Author** Michael Janner, Qiyang (Colin) Li, and Sergey Levine<br>
**Method** OFF-Policy / Model-Free<br>
**Action** Discrete <br>
**Code** [Original Implementation](https://github.com/jannerm/trajectory-transformer), [Better+Faster Implementation](https://github.com/Howuhh/faster-trajectory-transformer) <br>

#### Architecture
![architecture](https://people.eecs.berkeley.edu/~janner/trajectory-transformer/blog/architecture.png)

#### Core of Idea
 - <em>Formulate RL as sequence generation problem, and the goal of the Trajectory Transformer is to model the distribution over trajectories seen in a dataset. Frist the trajectories are tokenized, so for every dimension of every state and action we are going to discretize that dimension and then we model the discretized distribution for every "token". This is very nice becuase once we discretize per token, we can represent very complex distribution with a very simple and generic model. Altough, the sequence length becomes very large, but the modeling is simple and we can leverage powerful sequence models like Transformers which can represent these distributions very accurately. This gives us the ability to generate high probability trajectories and this is combined with beam search to consider among these highly probable trajectories which ones yields the most reward.</em>
 - **Step 1: Density Modeling**<br>
      - Initial Trajectory<br>
     $$\mathbf{\tau} = (\mathbf{s_1}, \mathbf{a_1}, r_1, \mathbf{s_2}, \mathbf{a_2}, r_2,..., \mathbf{s_T}, \mathbf{a_T}, r_T)$$
      - Tokentized Trajectory
     $$\mathbf{\tau} = (...,s_t^1, s_t^2,...,s_t^N, a_t^1, a_t^2,...,a_t^M, r_t,...)$$
      - Model Represents
     $$P(\tau)$$ 
     $$P(s_{1:T}, a_{0:T}, r_{0:T}|s_0)$$
 
 - **Step 2: Planning**<br>
     ![TT Planning](https://github.com/iamsiddhantsahu/RL-SequenceModels/blob/main/TT_Planning.png)
     
     - During planning we are trying to find trajectories that give us high reward (beam search) **AND** from the trajectories that the Trajectory Tranformer thinks are actually likely to be feasible trajectories.
     - If we didn't have the second term in the equation, using beam-search as a reward-maximizing procedure would lead to a "Myopic" behaviour or in other words the model would prone towards having reward now then reward later.

#### Drawbacks
1. Slow and Computationaly Expensive, thus NO real time control.
2. Discretization of continous domain imposes upper bound to prediction precision.

<!-- #### Questions -->
<!-- 1. Should we model RL as permutation invariant? Or in other words, does the order of state, action and reward matter in RL? If so, why do the authors trained on sequences of states, actions, and rewards treated interchangeably? -->


