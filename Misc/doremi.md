# DoReMi, Optimal data mixtures

## Intro
 - data mixtures directly affect model performance
 - the right mixture is often unclear
 - instead of optimizing domain weights for downstream tasks, optimize for the domains its meant to be trained on
 - optimizes for the worst-case excess loss
 - DoReMi loop
    - train a small reference model with regular data (280M)
    - train a small proxy model with DRO for domain weights
    - train the LLM on properly weighted domains
 - The excess loss is the diff between ref model loss and DRO
 - Use DRO-LM, get the new dataset based of those weights

## Doremi
 - get the data distribution, or the uniform data distribution
 - Obtain a small reference model
 - group DRO model for domain weights
 - train LLM with reweighted domains

## exp
 - got the same loss/ppl 2.6x fast, 1.6x better

## Future work
 - making this work for multiple modalities stabiliy?
 - future work would involve extrapolating domain weights from prev ones, 