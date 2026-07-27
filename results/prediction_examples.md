# Prediction Examples

## Correct Healthy Prediction

The uploaded healthy leaf was predicted as `Blueberry___healthy` with a
HEALTHY status and approximately 97% confidence. The screenshot was
extracted from the completed demo video.

## Begonia Failure Case

The uploaded polka dot Begonia was predicted as
`Strawberry___Leaf_scorch` with a DISEASED status and approximately 96.7%
confidence.

The Begonia is not one of the 38 supported PlantVillage classes. Its
natural white spots and real-world background created domain shift, so
the model matched the image to the closest known class even though the
plant appeared generally healthy.
