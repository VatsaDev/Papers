# Kosmos-1: Aligning Perception with Language Models 

## Intro
 - MLLM, vision+language
 - Increase in usability (API, robotics, Documents) 
 - Better reasoning, boosted by visual information
 
## Kosmos-1
 - Tokenization
    - text, <s></s> tokens
    - images <image></image>
 - Transformer with vision encoder
   - Magneto tranformer variant (more stable training and scaling?)
   - Xpos encodings (wonder how this compares to RoPE)
 - 1.3B/360B train tokens (small, but effectiveish for size) + 0.3b frozen clip, 1.6b total
 - scores above flamingo-9b, 5x smaller

# Kosmos-2: Grounding MLLMs
 - has bounding box capabilities, stronger grounding, much more detail oriented
 - making the bounding boxes
   - extracting nouns/terms
   - remove abstract ideas
   - use GLIP bounding modeled, keep captions with a higher than 65% confidence
 - for expanded visual descriptions, use SpaCy tools to expand thw words to sentences
 - split the image into bounding boxes PxP where each is a (w/h) and then the model outputs in format <box>loc1 loc2</box>, locs use p
 - The grounding and text references greatly increase answer accuracy
 - a finetune of Kosmos-1, on 25B more tokens, gains bounding, etc

# Kosmos 2.5: A Multimodal Literate Model
 - Reading text from text intensive images
 - image to markdown format text

## Future work
 - Scaling
 - Integrating speech and audio
 - mulitlanguage text from multilingual docs
 - more precise view of document, long context for multipage