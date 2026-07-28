# Pixel Predators: Plant Disease Classification

## Project Information

**Course:** ITAI 1378 Computer Vision  
**Project:** Midterm Blueprint  
**Tier:** Tier 1  

## Team Members

- Alexia Y. Chavez
- Elham Timory
- Tobias Chow


## Tier Selection

We selected Tier 1 because this project uses a pretrained image-classification model and transfer learning to create a practical application within our available time, experience level, and free computing resources.

## Problem Statement

Plant diseases can reduce crop production, damage food supplies, and cause financial losses for farmers and agricultural organizations. Farmers may rely on manual inspection or agricultural experts, which can take time and may not always be available. A fast image-based screening system can help identify possible plant diseases earlier.

## Solution Overview

We will create a plant disease classification application that accepts a leaf photo and predicts whether the leaf is healthy or affected by a specific disease. The application will return the predicted crop-condition label and a confidence score through a simple Gradio interface. This application is intended as a preliminary screening tool and not as a replacement for professional agricultural diagnosis.

## Application Flow

**Leaf photo → Image preprocessing → ResNet50 model → Disease or healthy label → Confidence score**

## Technical Approach

### Computer Vision Technique

The project will use **image classification with transfer learning**.

Image classification allows the system to examine a plant leaf image and assign it to one crop-condition category.

### Model

We will use **ResNet50**, a convolutional neural network pretrained on the ImageNet dataset.

Most of the pretrained backbone layers will initially remain frozen. The final classification layers will be fine-tuned using PlantVillage images so the model can predict plant diseases and healthy conditions.

### Frameworks and Tools

- Python
- PyTorch
- torchvision
- Google Colab
- Hugging Face Datasets or Kaggle
- Gradio
- Matplotlib
- scikit-learn

### Why This Approach Was Selected

Transfer learning allows us to reuse visual features that ResNet50 has already learned, such as shapes, textures, edges, and color patterns. This can reduce training time and computing requirements compared with training a deep neural network from the beginning.

PyTorch and torchvision will be used to prepare the data, fine-tune the model, and generate predictions. Gradio will be used to create the user interface for uploading leaf photos and viewing results.

## Data Plan

### Data Source

The project will use the public **PlantVillage dataset**.

Dataset information:

`https://www.tensorflow.org/datasets/catalog/plant_village`

The dataset is publicly available and already contains labeled images of healthy and diseased plant leaves. Our team will not need to manually label the full dataset.

### Rough Dataset Size

The complete dataset contains approximately **54,000 leaf images**.

If the full dataset requires too much memory or training time, the team will use a balanced subset containing approximately **10,000 to 15,000 images**.

### Labels

The dataset contains approximately **38 crop-condition classes across 14 crop species**.

Each label identifies both the crop and its condition.

Example labels include:

- Tomato healthy
- Tomato early blight
- Tomato late blight
- Apple healthy
- Apple scab
- Corn healthy
- Corn common rust
- Potato healthy
- Potato late blight

### Data Preprocessing

The images will be prepared using the following steps:

1. Resize each image to 224 × 224 pixels
2. Convert each image into a PyTorch tensor
3. Normalize images using ImageNet mean and standard deviation
4. Apply augmentation to training images
5. Divide the dataset into training, validation, and testing groups

Possible training augmentations include:

- Horizontal flipping
- Small rotations
- Random cropping
- Brightness adjustments
- Color adjustments

Augmentation will only be applied during training. Images uploaded to the final application will only be resized and normalized.

### Planned Data Split

- 70% training
- 15% validation
- 15% testing

The training set will teach the model. The validation set will help adjust model settings. The test set will measure the final performance on images the model has not seen during training.

More information is available in [`data/README.md`](data/README.md).

## Success Metrics

### Primary Metric

The primary success target is:

> **At least 90% top-1 test accuracy**

This means the final model should correctly classify at least 90 out of every 100 unseen test images.

### Secondary Metric

The secondary success target is:

> **Prediction time under one second per image**

The application should return the predicted plant condition and confidence score within one second after processing the image.

### Supporting Evaluation

The team will also review:

- Precision
- Recall
- Macro F1-score
- Confusion matrix
- Confidence scores
- Correct predictions
- Misclassified images

These measurements will help identify which crop-condition classes perform well and which classes require additional improvement.

## Six-Week Milestone Plan

| Week | Phase | Main Tasks |
|---|---|---|
| Week 1 | Create the Team | Form the Pixel Predators team and discuss possible computer vision project ideas |
| Week 2 | Develop the Blueprint | Review the project requirements and begin the proposal slides, GitHub repository, and README |
| Week 3 | Choose the Project and Dataset | Select Plant Disease Classification and confirm the PlantVillage dataset |
| Week 4 | Refine the Project | Improve the project scope, assign team titles, divide responsibilities, and organize project tasks |
| Week 5 | Improve the Project | Refine the technical approach, success metrics, risks, resources, and application workflow; begin a small pretrained-model demonstration |
| Week 6 | Present and Submit | Complete the proposal PDF, GitHub repository, presentation, and final midterm submission |

## Risks and Backup Plans

### Risk 1: Controlled Dataset Images

Many PlantVillage images have simple backgrounds and controlled lighting. Because of this, the model may perform well on the dataset but may not perform as well on outdoor leaf photos.

**Plan B:**

- Apply stronger image augmentation
- Test the application on several real leaf photos
- Review incorrect predictions
- Clearly state that the application is a preliminary screening tool

### Risk 2: Dataset Size and Colab Limits

The complete PlantVillage dataset may require more memory, storage, or training time than the free Google Colab environment provides.

**Plan B:**

- Use a balanced 10-class subset
- Reduce the batch size
- Reduce the number of training epochs
- Save model checkpoints to Google Drive
- Use Kaggle Notebooks as a backup

## Resources and Estimated Cost

### Compute Resources

- Google Colab free tier
- Kaggle Notebooks as a backup
- Google Drive for saving model checkpoints

### Software Resources

- Python
- PyTorch
- torchvision
- Hugging Face Datasets
- Gradio
- Matplotlib
- scikit-learn

### Data Resources

- Public PlantVillage dataset
- Optional real leaf photos for additional testing

### Estimated Cost

| Resource | Estimated Cost |
|---|---:|
| PlantVillage dataset | $0 |
| Google Colab | $0 |
| Kaggle Notebooks | $0 |
| Software libraries | $0 |
| APIs | $0 |
| **Total Estimated Cost** | **$0** |

The project is designed to be completed using public data, open-source software, and free computing resources.

## Training Setup

Framework: PyTorch

Model: ResNet50

Loss function: Cross-entropy loss

Optimizer: Adam

Image size: 224 × 224 pixels

Output classes: 38

Interface: Gradio

Training environment: Google Colab

Image Preprocessing

The images were prepared using the following steps:

Resize each image to 224 × 224 pixels

Convert the image into a PyTorch tensor

Normalize it using ImageNet mean and standard deviation

Apply augmentation only to training images

Divide the data into training, validation, and test groups

Training augmentation included small rotations, horizontal flipping, cropping, and color changes. These changes helped the model learn from more varied examples.

Final Results

The model was evaluated on 3,269 held-out test images.

Metric

Final Result

Test accuracy

97.71%

Macro F1-score

0.9773

Weighted F1-score

0.9770

Number of classes

38

Test images

3,269

Lowest-performing class

Tomato Early Blight

Lowest class F1-score

0.8984

The final model exceeded our original target of at least 90% test accuracy and a macro F1-score of at least 0.88.

Lowest-Performing Class

The lowest-performing class was Tomato___Early_blight.

Precision: 0.8660

Recall: 0.9333

F1-score: 0.8984

Support: 90 images

The model likely confused Tomato Early Blight with other tomato diseases that have similar brown spots, yellow areas, and damaged leaf patterns.

Successful Prediction

During the demo, the model correctly classified a healthy leaf as:

Blueberry___healthy

The application also returned a HEALTHY status and a high confidence score.

Failure Case

We tested the model with a healthy polka dot Begonia. The model incorrectly classified it as a diseased PlantVillage class.

This happened because:

Begonia is not one of the 38 supported classes

Its natural white spots resembled disease symptoms

The image had a real-world background

The model was required to choose one of its known classes

This failure demonstrates domain shift and the limitations of closed-set classification.

Challenges and Fixes

Dataset Loading Problem

One PlantVillage dataset source did not load correctly in Google Colab because of a configuration problem.

Fix: We used a working Hugging Face dataset mirror and verified that it contained 38 classes.

Class Imbalance

Some crop-condition classes had more images than others.

Fix: We limited the maximum number of images selected from each class to create more balanced training, validation, and test subsets.

Real-World Images

PlantVillage images usually have simple backgrounds, while real phone photos may contain shadows, hands, pots, and multiple leaves.

Fix: We used image augmentation and included a real-world Begonia image as an honest failure case.

Limitations

The model supports only the 38 PlantVillage classes

It may make incorrect predictions for unsupported plant species

Real-world backgrounds and lighting can reduce performance

A high confidence score does not guarantee a correct prediction

The system does not provide professional treatment advice

The model does not currently have an “unknown” output class

Future Improvements

Future versions could:

Add more real-world leaf images

Include ornamental plants and naturally spotted healthy leaves

Add an unknown or unsupported-image option

Use leaf segmentation to reduce background distractions

Identify the plant species before predicting its condition

Improve confidence calibration

Test the model with outdoor farm images

## Final Presentation

[Download the Pixel Predators Presentation](./docs/FP_PixelPredators_Elham_ITAI1378.pdf)

## Demo Video

[![Watch/download the Pixel Predators Demo](/Demo/Demo.mp4)

## AI Usage

The team used ChatGPT to help review the project requirements, organize the proposal, improve grammar, explain computer vision concepts, revise the milestone plan, and prepare presentation notes.

All AI-assisted content was reviewed and revised by the team. The project decisions, technical approach, explanations, and final implementation will reflect the team members' understanding.

AI usage will continue to be recorded in [`docs/AI_usage_log.md`](docs/AI_usage_log.md).

