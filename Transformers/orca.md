# Orca

## Intro
 - llama 7b, 13b finetuned with GPT-4 synth data, achieve parity with gpt-3.5
 - popular datasets like sharegpt contam

## Data
 - data gen
    - take query response pairs and enhances them with information
    - labels like eli5, cot think step by step
    - scaling the amount of instruction data
    - multiple system instructions increases performance
    - increase scale by collecting from flan

# Orca 2

## Intro
 - improving the training data further, for more model gains
 - clear, logical data patterns, for better models
 - better data patterns in Orca 2, 
    - more intricate prompts designed for strategic behaviour, specific results, given to the better LLM, gpt-4
    - the smaller model is given the task+response, without the detailed prompt (prompt erasure)
    - reasons better, doesnt just copy style
 - Multi-stage tuning
    - standard instruction tunes 
    - Explanation tuning with orca-1 reasoning signals
 - Increase dataset size, by asking the same questions with a different system prompt, for a diverse number of ans per Q
 - some system prompts better than others (Hmm, get model to rank responses, then find the best system prompt for a question, get a retrieval system for the best sys prompt?)


## future work
 - making smaller models just as capable
