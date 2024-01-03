# Phi, Phi 1.5 textbooks

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
    - 20B tokens of pure textbooks, synth data in phi 1.5
 - filtering the code datasets
    - get the python subsets of the stack (35m)
    - send random samples (100k) to gpt-4 to rate for learning quality
    - train a random forest classifier
    - this approach already has a huge benefit to benchmarks (hmm possibly use the approach on diverse pretrain data? would need universal signal)
 - synth data generation needs diverse prompts to work, or it will be repetitive
    - heavy on natural language reasoning and explanations around code
 - Synth exercises
    - docsring with function, meant to align the model to its instructions
 - the model spikes after the instruction tuning, it may consolidate the models knowledge
 - using gpt-4 grading to see how well the model really codes, not just its outputs, more meaningful signal of model capabilities