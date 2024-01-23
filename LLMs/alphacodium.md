# Code Generation with AlphaCodium

## Abstract
 - Many NLP optimizations dont work for code
 - test-based code oriented iterative flow
 - eval on codeforces/codecontest

## Intro
 - correct solutions to a problem can be very different
 - LLMs can code, but often fail in the real world
 - IRL tasks more nuanced, specs that code must address
 - The CC dataset allowed for the evaluation on more complex tasks
 - Alphacode worked, but was too expensive and brute force for any real solution
 - alphacodium has a flow of fixing code against tests 
 - alphacodium loop
    - preprocess a problem
        - input, problem description, tests
        - problem reflection
            - describe the problem in bullet points, while the goal and input/outputs, rules, etc.
        - public test reasoning
            - explain why each test case leads to its outputs
            - proper reflection makes the problem easier, improves code
        - generate possible solutions (2-3)
        - rank solutions
            - Rank solutions on efficiency, simplicity, and robustness
        - additional ai tests
     - Code iterations
        - initial code
        - iterate on public tests
        - iterate on ai tests
        - final solution
 - AI tests are made because public tests arent fully comprehensive, and AI gen tests lowers the need for extrapolation, and helps further the AI, even if it doesnt fully understand the problem yet
 - code oriented tricks
    - YAML structured output
        - stops prompting black magic and allows for an easy layout of the problem
        - straight forward, code-like manner
        - YAML, is more nlp friendly than json, better standard?
    - bullet point analysis, encourages semantic reasoning
    - generating modular code
        - one giant function will suck compared to modular code, more buggy in long form
    - encourage exploration, postpone direct solutions
        - when directly asked things, it hallucinates
    - test anchors
 - using the flow boosts performance for all models
 - signifigantly less compute expensive, 4 orders of magnitude less calls

## Code contests dataset
 - Has many private test cases to migitate LLM leakage
 - LLMs dont often pay attention to small details
 - problems are, by definition, long and hard

## Design
 - flow relies on knowledge accumulation, works better going from easy to hard
 - Double validation technique, makes llms more ready to make choices
 - AI tests are tested against code that works for all public tests, to make sure the tests are valid

## what doesnt work
 - giving the model the error trace, no improv
 - complicated single prompts 
 - git traces
 - failed code