# Mamba

## Intro
 - most research is just based on the transformer and attention
 - SSMs (ex. S4)
    - SSMs combine CNNs, and RNNs
    - can be computed as a conv or an rnn, linear, near linear times
    - like RNNs, but all the inputs at the same time to compute the output, (rnn space, transformer perf)
    - all the hidden states are linear transformations in S4, like LSTM, but far less complex backprop
    - No time dependence compared to RNNs, so all the hidden states are effectivly the same without inputs, and can all be done in one computation
 - Some changes
   - selection: efficiently select certain inputs to focus/ignore
      - computation of different hidden states is data-dependant only
      - by parameterizing the Mamba matrices, the model chooses what to learn/ignore (Really useful for dense modalities like language/dna)
   - hardware optimized algorithim
      - run a GPU-efficient scan to caluculate all the hidden states
       - mamba hardware code splits between GPU HBM and SRAM? less stuff movement, faster
       - fused selective scan like flashattention for backward pass
       - paralell scan/prefix sum on all the matrices
      - computes the scan very efficiently, still linear, 3x faster on a100, avoids a100 IO, very fast training/inference
   - architecture:
      - take an S4 block, combine it with an transformer MLP to get a mamba block
   - large sequence lens:
      - works well on sequences up to 1M tokens (thats Entire codebases/book series ?? More multimodal data needed for these models)
       - the selectiveness in Mamba brings strong performance
 - SOTA for Genomics/Audio, scales to 1M tokens, and scores as well as transformers twice its size, 5x faster inference

## State space models
 - mamba parameters have more dimensions compared to S4, bigger
 - structure/dimensions
   - computing these efficiently means structuring the A matrix, diagonally
   - it has o(BLDN) time and space complexity
 - other SSMs
   - linear attention
   - H3
   - Hyena
   - retnet
   - rwkv

## Selective state space models
 - mamba sequences are a tradeoff between effectiveness and efficiency
   - smaller state, more compression, more efficient, less effective
   - bigger state, less compression, less efficient, more effective
 - The mamba models use selectivity, the context aware ability to focus/filter inputs
   - this works because the parts that deal with the hidden state, prop, and inputs, is all learnable matrices
 - State space architeture
   - with the rnn state -> input -> state
   - No time-step difference
   - S4 models have 4 parts with learnable parameters, in a learnable matrix
      - x: data dependant
      - A: how the hidden state is propogated
      - B: how much input is propogated
      - C: how the hidden state is processed into the output state
   - output is a linear function of hidden state
   - A, B are both discretized
 - all ssms are tradeoffs between hidden state and train time/cost, mamba maxes out hidden size for cost

## selective scan, accounting for hardware
 - in longer sequences, the rnn inference is better than conv inference
 - send parameters to SRAM, and send final values back to HBM, minimizing the IO time
 - the intermediate values are redone in HBM

## simplified SSM
 - H3 is the ssm basis
 - mamba block is H3+MLP
 - linear projections make most of the parameters, in ssm is small
 - the mamba block is repeated, with residual connects + normalization
 - Silu/swish activation
 - also uses layernorm like retnet
 
## Connection to Gating
 - effects of selective ssm
   - Variable spacing: allows the ability to filter noise tokens
   - Filtering context: SSSMs are easily able to reset when nesc. and so get better, the longer the ctx
   - SSSMs are better at keeping multiple statements in the ctx from bleeding together

## other model asp.
 - complex numbers help with continous modalities (audio, video), but not discrete ones (text, dna) (Hmm, so does Xval require complex nums in the model?)
 - 

