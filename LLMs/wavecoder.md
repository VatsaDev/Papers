# Wavecoder

## Intro
 - data collection pipeline
    - start with regular old code (Codesearchnet), filter through with code quality rules
        - code len between 50/800
        - also used codeAlpaca blacklist
    - embedding space, kcentergreedy, gets the raw core codeset
        - reduce training data amount, but still remain diverse
    - for Instruction data, define a task, llm zero-shot/few-shot
    - LLM discriminator checks output against its rules
    - good gens go in database, bad ones discarded
 - more diverse instructions, makes better performance
 - 4 code tasks
    - Code summarization
        - Instructional comments on how it works/usage
    - Code Generation
        - manuscript instruction/pseudocode, produce the proper code for it
    - Code Translation
        - language to language
    - Code Repair
        - repair potential issues in code/bugfix?

## future work
 - more tasks
 - interusage of tasks
 - more quality data