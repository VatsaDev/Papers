# MusicLM: Generating Music From Text

## Intro
 - text to audio
 - (also possible to do transformer with audio tokens?)
 - AudioLM, audio generation as a LM task
 - richer data, better outputs
 - (One model for music, TTS, etc?)
 - Text-audio pairs are rare
 - used a music-text model to generate text captions for audio, allowing them to use massive audio copora

## Model
 - Using semantic tokens (model long term structure) and acoustic tokens (neural audio codec)
 - symbolic representations (Midi, etc) can be useful for models