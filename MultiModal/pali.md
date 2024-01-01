# Pali: Multilingual VLM

## Intro
 - combine multiple languages with VLM
 - 13b lm + 4b ViT
 - new dataset webLi, multilingual+multimodal

## The model
 - Vit, encoder then decoder
 - data is a mixture of 8 pretrain tasks
    - text only
    - interleaved web
    - images+captions
    - object detection
    - etc..

## future work
 - more modalitites in more languages
 - more data