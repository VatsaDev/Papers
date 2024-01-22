# Deductive Closure Training of Language Models for Coherence, Accuracy, and Updatability

## Abstract
 - LLMs can generate factual text, they dont have a consistent world model (Hmm maybe because they happen to be trained on all of the internet? wonder what happens when everything is convered to one viewpoint by a llm or smth)
 - DCT (detective closure training) makes LLMs identify the contradictions and corellations in the text it makes
 - Can Globally reason over text, and finetunes on correct text
 - reasoning leveraged during training to improve reliability

## Intro
 - While LLMs cant verify text, they can find relations between text
 - They can identify logical/probablistic relations
 - deductive closure on a training set can be made depending on the initial information
 - In DCT, LLMs assign high probablities to a complete and consitent set of facts
 - DCT uses inference reasoning as training supervision
 - reason on which parts of the text are correct, then finetune on that
 - perform supervised adaptation for factuality
 - if the seed documents are provided by the model itself, then one can have unsupervised learning
 - LLMs can improve their own accuracy/updatability

## method
 - DCT begins with a couple seed documents
 - use the language model to generate additional text implied by the seed text, or contradicted by the seed text
 - versatile, works for statements, QA, multihop consequence
 - DCT identifies a subset of the generated text to be true
 - start by giving every document a truth score
    - use prompting to get a true/false
    - use LLM logits of the true false statements, after conditioning llm
 - finetune on true docs

## Analysis
 - After DCT, high prob logits tend to be the correct ones
 - Give it a Q with a correct QA pair to increase prob. of a correct answer

## Experiments
 - 10% increase in factual correctness
 - 15-30% acc. increase when finetuned on DCT data 
 - Reversal curse also sees a large increase in accuracy
 - The model can double check, incorporate prev info, and make novel inferences

