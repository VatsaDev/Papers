# A Survey on Data Selection for Language Models

## Intro
 - main challenge is to make a dataset optimal for something, performance, biases, etc
 - Data selection methods can help reduce dataset size, Integrity of val/train, reduce bias/toxicity
 - Important for LMs, multiple data stages, pretrain, instruction, alignment
 - With large amounts of text, the main goal is to filter and get rid of weaker data, so only the high quality remains
 - Data Diversification vs Pruning
     - Prune Data: Remove worse datapoints 
     - Diverse: Add datapoints to fix distribution

 - Text Data Filters: Pretrain
     - Start with language data filters
         - Keep a note on language quality, and the amount of data in each language, including code
         - try to keep utility functions fast, so that one can remain computationally efficient for trillions
         - try to keep the number of languages in one doc itself low, less noise
         - for low resource languages, using the URL as a filter can be better than using language detector models
         - use filenames for programming languages, some keywords, etc
     - Heuristics filters
         - Check code through for Boilerplate, errors, noise, etc
         - look through data for terrible stuff, like dashes/hashes everywhere, 
         - use sentence lentgh, and repetitiveness, statistics, etc
         - some common filters
             - webpages shorter than 5 sentences
             - docs between 50 and 100000 in len (wont be having the 100k anymore)
             - remove pages with a words to illicit ratio above a certain amount, as to avoid false positives/removing legal, etc
             - high repetition docs tend to suck, remove them
             - find good/valid math latex, tends to be useful
     - Data Quality filters
         - most often human written data that has been edited/reviewed
         - Common util functions
             - Fuzzy/Ngram matches docs against the high quality set to determine factualness and stuff
     - Domain specific data
     - Deduplication
         - bloom filters
         - check ngram similarity
         - Check hash similarity, minhashlsh
         - check fuzzy/cosine similarity
     - Toxic and explicit content
         - URL filters
         - blacklist check
         - content checker
         - Replace PII with special tokens
     - Data mixing
         - run doremi/doge

 - Text Data filters: Instruct
     - multitask distributions are really important here
     - Use multiple chat templates throughout the dataset to be chat immune
     - synthetic data

 - VLM tasks
     - may alt text of web images
     - synthetic images 
     - find playthrough videos off yt, etc, make a video world model