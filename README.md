# RL-SequenceModels
This repository contains some recent research work on RL and Sequence Models



### TT - Trajectory Transformer

**Paper** [Offline Reinforcement Learning as One Big Sequence Modeling Problem](https://proceedings.neurips.cc/paper/2021/file/099fe6b0b444c23836c4a5d07346082b-Paper.pdf)<br>
**Author** Michael Janner, Qiyang (Colin) Li, and Sergey Levine<br>
**Method** OFF-Policy / Model-Free<br>
**Action** Discrete <br>
**Code** [Original Implementation](https://github.com/jannerm/trajectory-transformer), [Better+Faster Implementation](https://github.com/Howuhh/faster-trajectory-transformer) <br>

#### Core of Idea

#### Drawbacks
1. Slow and Computationaly Expensive, thus NO real time control.
2. Discretization of continous domain imposes upper bound to prediction precision.

#### Questions
1. Should we model RL as permutation invariant? Or in other words, does the order of state, action and reward matter in RL? If so, why do the authors trained on sequences of states, actions, and rewards treated interchangeably?


