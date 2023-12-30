# MusicLM: Generating Music From Text

## Intro
 - text to audio
 - (also possible to do transformer with audio tokens?)
 - AudioLM, audio generation as a LM task
 - richer data, better outputs
 - (One model for music, TTS, etc?)
 - Text-audio pairs are rare
 - used a music-text model to generate text captions for audio, allowing them to use massive audio copora

## Method
 - Using semantic tokens (model long term structure) and acoustic tokens (neural audio codec)
 - symbolic representations (Midi, etc) can be useful for models
 - Tokenization
    - MuLan Text embeddings
    - soundstream
    - w2v bert
 - Semantic work, then acosustic work

## Future work
 - lyrics generation, lyrics tokenization?
 - higher order of music, work on music flow, conductor tones?
 - RL tune, audio version of chatgpt, produces human pref audio?