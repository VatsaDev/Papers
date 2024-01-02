# xVal

## Intro
 - LLMs cant do math
 - weak against simple arithmetic like multidigit multiplication
 - some methods include digit by digit tokenization, scientific format
 - the cosine distance of numbers can be used to show their actual difference, and so transformers can learn math through matrix multiplication, but its only somewhat effective
 - LLMs exploit incorrect patterns, due to just needing the answers (Fix that? step by step detailed out for the model helps, more scratchpads, drop loss as low as possible?)

## Model
 - helps with numbers being continuois to do math, numbers are encoded continously in xVal
 - encode the magnitude of numerical values, orienting them in a learnable direction
 - All numbers and mathematical calculations compressed to a single token [NUM]
 - all the num token embeddings are changed by the number, reflects a learnable value for the embedding space
    - when given an alpha-numeric prompt, all the numbers are removed and replaced with NUM
    - numbers stored in a sep list
    - make embeddings
    - now multiply each NUM token by the numerical values it was supposed to be
 - Implicit Normalization
    - the changed embeddings have a pos vector added on, then layer norm
    - normalizes the embddings that have been changed
    - pos vector isnt related to the math, but it still follows the direction it should be in
 - decoding is done with a different head for numerical values, to keep the model end-to-end cont.
    - the math head decodes to the value of the num token, trained with MSE loss
    - since it remains cont. better overall for out of dist data

## Comp
 - non-single encoding for nums ruins mathematical capabilities
 - maintains 99.6% acc on 5 digit multiplication
 - 99% accuracy for pemdas applications
 - sota loss on temp prediction, planetary orbits
 - some faliure modes, includes not predicting a number when they should, also fails with learning distributions occasionally


## Future work
 - Making the model work better for higher mathematics, learning calculus?
 - normalization in the embeddings is difficult, large numbers are too much, little nums to small
    - try the fourier on the log of the num to combat this
