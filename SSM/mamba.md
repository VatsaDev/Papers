# Mamba

## Intro
 - most research is just based on the transformer and attention
 - SSMs combine CNNs, and RNNs
 - can be computed as a conv or an rnn, linear, near linear times
 - great for long range predictions, scales linearlly
 - Some changes
   - selection: efficiently select certain inputs to focus/ignore
      - by parameterizing the Mamba matrices, the model chooses what to learn/ignore (Really useful for dense modalities like language/dna)
   - hardware optimized algorithim
      - computes the scan very efficiently, still linear, 3x faster on a100, avoids a100 IO, very fast training/inference
   - architecture:
      - take an S4 block, combine it with an transformer MLP to get a mamba block
   - large sequence lens:
      - works well on sequences up to 1M tokens
 - SOTA for Genomics/Audio, scales to 1M tokens, and scores as well as transformers twice its size

## Notes
 - diff from competitors (RWKV, Hyena, etc)
 - SSMs (ex. S4)
    - like RNNs, but all the inputs at the same time to compute the output, (rnn space, transformer perf)
    - all the hidden states are linear transformations in S4, like LSTM, but far less complex backprop
    - No time dependence compared to RNNs, so all the hidden states are effectivly the same without inputs, and can all be done in one computation
 - Mamba uses selective ssms
    - reduces the use of the linear hiddens in S4
 - computation of different hidden states is data-dependant only
 - run a GPU-efficient scan to caluculate all the hidden states
 - combine SSMs with MLP, transformers blocks, etc
 - attention free, not quadratic
 - performs better for long sequence data
 - the selectiveness in Mamba brings strong performance
 - can stand a 1M sequence lentgh (in nlp, thats Entire codebases/book series ?? More multimodal data needed for these models)
 - a Mamba layer is the combination of H3 layer + MLP, with the selective ssms
 - State space architeture
   - with the rnn state -> input -> state
   - discrtization, non-cont. values
   - S4 models have 4 parts with learnable parameters, in a learnable matrix
      - x: data dependant
      - A: how the hidden state is propogated
      - B: how much input is propogated
      - C: how the hidden state is processed into the output state
   - output is a linear function of hidden state
 - mamba parameters have more dimensions compared to S4, bigger
 - mamba hardware code splits between GPU HBM and SRAM? less stuff movement, faster
 - fused selective scan like flashattention for backward pass
 - paralell scan/prefix sum on all the matrices
