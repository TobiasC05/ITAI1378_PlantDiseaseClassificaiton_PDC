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

## Expected Final Application

The final proof of concept should allow a user to:

1. Upload a plant leaf image
2. View the uploaded image
3. Process the image using the trained ResNet50 model
4. Receive a predicted crop-condition label
5. View the model confidence score

The final project should also include:

- A working Gradio interface
- Model evaluation results
- A confusion matrix
- Examples of correct predictions
- Examples of incorrect predictions
- Updated GitHub documentation
- A final demonstration and presentation

## Final Presentation

[Download the Pixel Predators Presentation](./docs/FP_PixelPredators_Elham_ITAI1378.pdf)

## Demo Video

[![Watch/download the Pixel Predators Demo](/Demo/Demo.mp4)

## AI Usage

The team used ChatGPT to help review the project requirements, organize the proposal, improve grammar, explain computer vision concepts, revise the milestone plan, and prepare presentation notes.

All AI-assisted content was reviewed and revised by the team. The project decisions, technical approach, explanations, and final implementation will reflect the team members' understanding.

AI usage will continue to be recorded in [`docs/AI_usage_log.md`](docs/AI_usage_log.md).

## Project Status

- [x] Team created
- [x] Blueprint started
- [x] Project selected
- [x] Public dataset identified
- [x] Technical approach selected
- [x] Success metrics established
- [x] Risks and backup plans identified
- [x] Midterm proposal completed
- [ ] First working model demonstration
- [ ] Dataset preprocessing
- [ ] Model training
- [ ] Model evaluation
- [ ] Gradio application
- [ ] Final demonstration
- [ ] Final presentation
