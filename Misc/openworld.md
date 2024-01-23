# Describe, Explain, Plan and Select: Planning with LLMs Enables Open-World Agents

## Abstract
 - task planning for LLMs is hard, but boils down to two things
     - executing plans in an open world enviorment (acc. multi-step reasoning)
     - vanilla planning doesnt really consider task difficulty
        - bad at ordering paralell subgoals
        - hard to judge the feasibility of a plan
 - DEFS, describe explain plan select
 - planning approach with error correction
     - able to describe its problem solving
     - can explain the feedback of failures
     - better goal selection, ranks goals with estimated steps to completion
     - refines initial plan

## Introduction
 - Inner LLM monologing/thoughts might be important
 - The more open the enviorment, the faster planning rates plunge, due to more info with complex relations
 - even the simplest goals have multiple complex paths
 - (On goal completion, make an LLM state goal completion requirements, in json vals, then compare real values against that)

## Reliable planning
 - Function calling can help with describing a scene and planning actions, its a clear syntax to get information, and return actions
 - Considering the open world enviorment is really important, as biomes, etc can also influence your actions
    - help that by defining loose goals, like asking for an item, and letting the LLM figure the best course of action for it, like asking for wood over oak wood
 - Wonder how more minecraft knowledge affects the LLMs, like having access to the MC wiki for optimal mine depths and stuff

## Ablations and limitations
 - more concurrent goals are harder execute at the same time
 - currently uses closed source LLMs (Their function calling means a great chance of moving towards OH-2)
 - The models step by step planning may make it forget future goals (going top down to break tasks should help)
 - Model never met any deadends, and so no info on that, yet real life has many