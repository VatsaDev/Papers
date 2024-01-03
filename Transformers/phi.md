# Phi, textbooks

## Intro
 - uses transformers
 - data quality is important
 - low size high quality data can result in powerful small models

## data
 - textbook data
    - synth gpt data, high quality, with predictable tokens
    - also using large amounts of internet textbooks
    - fine-tune on textbook exercises data
 - displays emergent properties, even though its really small
 - the code exercises were the really important point, they doubled performance, when the regular code textbooks were in the +5-10% range
    - raw code and code in general wont teach the model to plan arithmetically, it needs the reasoning and step by step breakdown
    - they also fail to teach the model about coding basics
    - not self contained, the model isnt learning the whole context and yet has to predict it
    - many examples arent real useful code, but just boilerplate
 - three main datasets
    - filtered code dataset (6B tok)
    - synth textbook dataset (1B tok)
    - synth exercises dataset (180m tok)
 - filtering the code datasets
    - get the python subsets of the stack (35m)
    - send random samples (100k) to gpt-4 to rate for learning quality
    - train a random forest classifier
    - this approach already has a huge benefit to 