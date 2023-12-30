# Unified-IO 2: Autoregressive multimodal models

## Intro
 - Has Video, Text, audio, vision, Action, input/output modalities
 - larger world model, all the senses support each other, raise overall perception
 - Hard to encode and decode all modalities
 - 7b model 600TB of pretrain data
 - Arch changes
    - 2d rotary embeddings
    - QK normalization
    - scaled cosine attention mechanisms on the perceiver resampler
 - for instruction tuning, synthetic data created where data was low in modalities combinations (image-audio, audio-action? etc?)

## Approach
 - VQ-Gan decoder for image/audio?
 - one encoder-decoder transformer, everything is tokenized into one embedding space
 - Tokenization
    - Text with llama tokenizer, 
    - Sparse Struc. (keypoints, bounding boxes, cam poses, etc), discretized, then turned into one of the 1K tokens added to llama tokenizer
        - coords [x,y] 
        - bounding boxes [(x1,y1),(x2,y2)]
        - 3D cuboids are 12 tokens, represent center, depth, box dimensions, rotation
    - Action represented with special tokens
    - Images use a ViT, get the patches from second and penultimate layers to get low+high level info, those patches pass through a linear layer for embeddings
    - Images generated -> VQ-Gan turning images to discrete tokens, which were added to the tokenizer, ~16k tokens from the 8x8 patchs?
    - per pixel labels, allow for segementation, model gives a binary mask, depth, etc
    - Audio is turned into a spectogram, 4s at a time, then they use an audio spectrogram transformer, ViT makes discrete vals, tokens added to tokenizer(~8k)
    - use a perciever resampler, to reduce image and audio token size (32 images, 16 audio)
    - eight special tokens for marking modality starts and ends
 - Rope at each transformer layer, 2 dimensions for rope non text modalities
 - MHA logits very high with multiple modalitites, so apply layernorm to Q and K before dot-product
 - normalized perciever with scaled cosine attention greatly stablizes everything
 - fp32 needed for logits, instable below, updating the transformer+ViT+ast is unstable, so ViT and Ast are only changed during finetune
 - uses UL2 mixture of denoisers
 - adafactor optimizer (look into that, what are the pros/cons)   
 - Instruction Tuning
   - Text - regular instruction dataset
   - Images - images edited/with filters, some pretrain restablished as instruct, inpainting, segementation, VQA etc
   - audio - Audio from instruction
   - Video, video understanding 

## future work
 - scaling model
 - better data
 - trimming/simplifying arch


