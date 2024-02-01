# A recipe for training NNs

## NNs are leaky abstractions
 - many libraries will make any NN with ~30 lines of abstractions
 - not like regular code where it works all the same out of the box for everyone
 - NN are not really off the shelf useable
 - NN methods dont magically work, you have to understand them to use them, if you dont, usage will be difficult

## NNs fail silently
 - NNs dont really give exceptions, or errors
 - everything can be syntax correct, but it fails in other ways
 - error space is large/logical 
 - most of the time an NN will train silently and worse

## The recipe
 - Throughly inspect the Data, spend hours in the data looking for distributions, patterns
 - if the nn gives a prediction far from the dataset, somethings wrong
 - look for duplicates, noisy labelling
 - make simple code to search/filter/sort all aspects of the dataset
 - outliers can often be low quality/removable stuff

## setup training skeleton
 - fix random seed: helps maintain consistency 
 - simplify: base model only, no data augumentation, 
 - add sig. digits to eval: plot test loss on the entire training set
 - verify init loss: verify that the loss is starting at the correct values for that nn type
 - initialize hyper params well, set biases to match data better
 - overfit a batch to make sure its working
 - verify that training loss decreases overtime

## Overfit
 - pick a simplistic model arch, dont go crazy
 - adam/adamw is a safe optimizer
 - complexify one thing at a time, make sure everything else still works
 - be careful with LR decay and know your current lr

## regularize
 - get more data, as much as possible
 - data augumentation
 - finetuning instead
 - dropout
 - weight decay
 - larger models

## Tune
 - tune hyperparams
 - more training will help most of the time


