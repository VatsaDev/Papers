# deepseek: scaling models with longtermism

## Intro
 - scaling laws from 7b to 70b analysis
 - been building an in house 2-trillion token dataset (Eng+chinese)
 - use SFT and DPO

## Deepseek dataset
 - all the cc dumps and dedup is much more beneficial than dedup 1 dump, 91% dedup for all dups
 - BPE, but charecters from different langs/other are not allowed to merge (chinese, english, punctuation), 100k tokenizer size
 - LLama based
 - cosine Lr and multistep Lr result in similar end perf, but multistep lr ratios can lead to better perf.
 - math finetuning data as a percentage of the dataset tends to increase model repetitiveness, stopped by using a two stage version with math sft and further DPO

## future work
 - code intelligence and MoE
 - Better dataset
 - RL reasoning boost