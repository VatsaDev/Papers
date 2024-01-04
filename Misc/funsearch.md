# Funsearch: Mathematical discoveries from program search

## Intro
 - many math problems are easy to evaluate, but hard to solve
 - Funsearch improves over best known solutions to such probs
 - solving open problems requires new solutions
 - funsearch finds new results for open probs, and discovers new Algos
 - surpassed SOTA, meaning these are true results, not LLM memories
 - combines an LLM with an evaluator, to guard against weird/incorrect solutions
 - evolving low score programs to high scoring programs
 - Action points
    - sample the best performing programs and feed them back to the llm (aka. Best shot prompting)
    - start programs as a skeleton(boilerplate), evolve the priority function used to make descisions
    - mantain a large pool of diverse programs using island-evo to encourage exploration, avoid minima
 - more interpreable than usual, as it gives a program, not an output

## funsearch
 - give the function to funsearch by giving it the evaluate code, and performance jumps when given an initial boilerplate
 - LLM doesnt matter as long as its trained on lots of code
 - programs scored by evaluator
 - db with all the correct programs
 - 