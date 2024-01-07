# Monarch structured matrices

## Intro
 - dense weight matrices are expensive
 - lighter structured ones, sparse/lowrank/fourier
 - structured matrices tend to either be inefficient or unexpressive
 - The work introduces monarch matrices
    - 2x as fast as regular matrices in GPT-2 training
 - most sparse methods (pruning, etc) deal in reducing flops, but slow train time
 - E2E 2x speedup
 - spare to dense and dense to sparse possible
 - based on butterfly matrices, inspired by fft
 - many matrixes can be rewritten as monarch matrixes
 - uses O(n√n) time complexity, but batch mm makes it really fast

## Future work
 - more sparse model work