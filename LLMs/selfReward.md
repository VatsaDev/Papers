# Self-Rewarding Language Models

## Abstract
 - Superhuman models, need superhuman feedback (Azero self play for LLMs?)
 - Iterative DPO, Better at making good outputs and rewarding itself
 - The model can be a great performer and a great judge

## Intro
 - Approaches like SFT, RLHF, DPO, are all blocked by data quality
 - Have a self improving reward model, live update
 - self rewarding language models, with two functions
    - be instruction following language models
    - can generate and evaluate new instructions to add to the training set
 - feedback loop
   - model makes new instructions
   - model makes multiple responses
   - model ranks the answers (LLM as a judge prompting)
   - this is turned into a DPO dataset, and the model is DPO trained
 - start with llama 2 70b, and seed with OASST. (saturates in real world tasks, but wonder if better start like a Mixtral model with ultrafeedback, means less time to hit the same cap or a higher cap to reach)

## Process
 - Iterative DPO models trained on the LLM as a judge
 - It can also be a reward model because it is the model that was improved
 - Generate new prompts by few shot prompting with a couple prompts
 - form preference pairs, check with highest and lowest scores for a prompt (Hmm, numerical scoring was shown to suck, so maybe have muliple categorys to evaluate with several word based categories, will help?)
 - new prompts made with fixed llama 2 70b, but evolving model probably makes better prompts?
 - DPO is better than positive examples only
 - beats all models on alpacaeval except gpt-4 and mistral medium. (Hmm, need more benchmarks, GPT-4 grader isnt everything, also the model prefers its outputs, and this model started with gpt-4 outputs. also maybe mistral medium has large amounts of GPT-4 data? )

## limitations and conclusions
 - intresting work as it could mean beyond human expansion
 - Needs more work on the saturation and scaling laws of this technique
 - increase in response lentgh, and resp. len and answer quality are often connected
 - needs more benchmarks
 - reward hacking by the LLM may also be occuring (obama pats obama meme here lmao)
