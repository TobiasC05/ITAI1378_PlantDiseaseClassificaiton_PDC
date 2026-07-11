# Data Plan

## Dataset Name

PlantVillage Dataset

## Dataset Type

This project will use a public dataset. The dataset is not self-collected
or synthetically generated.

## Dataset Source

The PlantVillage dataset is publicly available through TensorFlow
Datasets and the original PlantVillage GitHub repository.

Main dataset page:

[PlantVillage on TensorFlow Datasets](https://www.tensorflow.org/datasets/catalog/plant_village)

Original image repository:

[PlantVillage Dataset on GitHub](https://github.com/spMohanty/PlantVillage-Dataset)

## Approximate Size

The dataset contains approximately 54,000 images of healthy and diseased
plant leaves.

If the full dataset is too large for free Google Colab resources, the
team will use a balanced subset of approximately 10,000 to 15,000 images.

## Labels

The dataset contains 38 crop-condition classes across 14 crop species.

Each label includes the crop name and its condition.

Example labels include:

- Tomato healthy
- Tomato early blight
- Tomato late blight
- Apple healthy
- Apple scab
- Corn common rust
- Potato healthy
- Potato late blight

## Planned Data Split

The dataset will be divided into:

- 70% training
- 15% validation
- 15% testing

The training set will be used to train the model. The validation set will
be used to adjust model settings. The test set will be used to measure
the final model performance.

## Preprocessing Plan

The images will be prepared using the following steps:

1. Resize each image to 224 × 224 pixels
2. Convert the images into PyTorch tensors
3. Normalize the images using ImageNet values
4. Apply augmentation to training images
5. Organize the images into training, validation, and test sets

Possible augmentation methods include horizontal flipping, small
rotations, random cropping, brightness adjustments, and color changes.

## Storage Plan

The full dataset will not be uploaded directly to GitHub because it is
too large.

The dataset will be accessed through TensorFlow Datasets, Kaggle, or the
original PlantVillage repository. Large files and model checkpoints may
be stored in Google Drive or Google Colab.
