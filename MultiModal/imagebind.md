# Imagebind

## Intro
 - joint embedding space between six different modalities
    - Images
    - Text
    - IMU
    - audio
    - depth
    - thermal
 - compatible with vlms, extends the models capabilities
 - all the modalities are interconnected, its possible to use (imu <-> depth), (thermal <-> text), etc

## Imagebind
 - combine webscale data and naturally occuring pairs
 - the joint embedding space allows implicitly applying to text
 - contrastive learning for pairs
 - learns a single joint embedding at a time, between images and another modality
 - transformers for all modalities
   - regular transformer for text
   - ViTs for images, depth, thermal, etc
   - IMU is conv into a sequence
 - has emergent classification abilities

## Future work
 - combine with LLMs, future modalities