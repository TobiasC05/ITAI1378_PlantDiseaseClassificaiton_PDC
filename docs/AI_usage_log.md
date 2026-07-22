# AI Usage Log

## 1. Comparing Two Project Ideas

- **Date**: July 9, 2026
- **Tool Used**: ChatGPT, Claude
- **Question Asked**:  
  "Can you compare our two project ideas, Plant Disease Classification and Soccer datasets, based on dataset availability, technical difficulty, training time, evaluation methods, and suitability for a semester computer vision project?"

- **AI Suggestion**:  
  The AI suggested comparing the projects using common criteria instead of selecting one based only on interest. It recommended considering the availability and quality of labeled images, the number of object classes, expected computing requirements, project scope, and whether the final results could be clearly demonstrated. In this case, we chose Plant Disease Classification due to the easy-to-read dataset and information.

- **What I Learned**:  
  I learned that a good project idea must be realistic within the available time and resources. A more complicated project is not always better if the dataset is difficult to prepare or the model requires excessive training time.

- **How I Applied It**:  
  Our group used the comparison criteria to discuss the advantages and disadvantages of both projects and select the project that was more practical and achievable.

---

## 2. Understanding Object Detection and Image Classification

-  **Date**: July 10, 2026
- **Tool Used**: Claude
- **Question Asked**:  
  "Can you help us sort our project notes and course requirements into clear sections for the proposal?"

- **What the AI Suggested**:  
  Claude suggested organizing the information into the problem, proposed solution, technical approach, dataset plan, success metrics, milestone plan, risks, and required resources.

- **What I Learned**:  
  I learned that organizing the proposal around the rubric makes it easier to verify that all required areas are covered. It also helps the audience follow the project from the problem through the proposed implementation.

- **How I Applied It**:  
  We reorganized our existing team notes into eight presentation sections and checked that each section addressed a project requirement.

---
## 3. Classification Versus Object Detection

- **Date**: July 10, 2026
- **Tool Used**: ChatGPT
- **Question Asked**:  
  "Should our plant disease project use image classification or object detection?"
  - **What the AI Suggested**:  
  ChatGPT explained that image classification assigns one condition label to the complete leaf image, while object detection identifies and locates multiple objects using bounding boxes.

- **What I Learned**:  
  I learned that image classification matches our project because our intended output is one crop-condition label and a confidence score for each uploaded leaf image.

- **How I Applied It**:  
  We selected image classification rather than object detection or segmentation and adjusted the project scope to match the Tier 1 requirements.

---

## 4. Selecting ResNet50 and Transfer Learning

- **Date**: July 10, 2026
- **Tool Used**: Claude
- **Question Asked**:  
  "Can you explain whether ResNet50 transfer learning is appropriate for our PlantVillage project?"

- **What the AI Suggested**:  
  Claude explained that ResNet50 is already trained on ImageNet and has learned useful general image features. It suggested freezing most of the pretrained layers and replacing or fine-tuning the final classifier for the plant-disease categories.

- **What I Learned**:  
  I learned that transfer learning allows us to reuse previously learned visual features rather than training a convolutional neural network entirely from the beginning.

- **How I Applied It**:  
  We selected ResNet50 as our proposed feature extractor and planned to fine-tune the final classification layers using PyTorch and torchvision.

---

## 5. Planning the Dataset Preparation

- **Date**: July 10, 2026
- **Tool Used**: Claude
- **Question Asked**:  
  "How should we prepare and divide the PlantVillage dataset for ResNet50 training?"

- **What the AI Suggested**:  
  Claude suggested resizing images to 224 by 224 pixels, applying ImageNet normalization, using augmentation only on the training set, and keeping validation and test images unchanged.

- **What I Learned**:  
  I learned that augmentation should only be applied to training data because changing validation or test images could make the evaluation less consistent. I also learned that ResNet50 expects the same normalization format used during its ImageNet pretraining.

- **How I Applied It**:  
  We proposed a 70% training, 15% validation, and 15% test split. Our planned training augmentations include flipping, rotation, and color jitter.

---

## 6. Creating the Working Jupyter Notebook

- **Date:** July 22, 2026
- **Tool Used:** ChatGPT

### Question Asked

> Can you help us create a complete Jupyter Notebook for our Plant Disease Classification project using PyTorch and ResNet50?

### What the AI Suggested

ChatGPT suggested organizing the notebook into clear sections for environment setup, dataset loading, image preprocessing, model creation, training, validation, evaluation, and prediction.

### What I Learned

I learned that a machine learning notebook should follow a logical order because later steps depend on variables and results created in earlier cells.

### How I Applied It

We created a structured Jupyter Notebook with explanations and executable code cells that can be run in order in Google Colab.

---

## 7. Loading and Organizing the PlantVillage Dataset

- **Date:** July 22, 2026
- **Tool Used:** ChatGPT

### Question Asked

> How can we load and organize the PlantVillage images so they can be used by a PyTorch model?

### What the AI Suggested

ChatGPT suggested loading the images by class, checking the available disease categories, applying a consistent random seed, and separating the images into training, validation, and testing groups.

### What I Learned

I learned that the dataset folders and class labels must be organized correctly before PyTorch can connect each image with the correct target label.

### How I Applied It

We added dataset-loading code, displayed the detected classes, and created separate datasets and data loaders for training, validation, and testing.

---

## 8. Configuring ResNet50 for Plant Disease Classification

- **Date:** July 22, 2026
- **Tool Used:** ChatGPT

### Question Asked

> How do we modify a pretrained ResNet50 model so it can predict our plant disease categories?

### What the AI Suggested

ChatGPT suggested loading the pretrained ResNet50 weights, freezing most of the existing feature-extraction layers, and replacing the final fully connected layer with a new layer matching the number of classes in our dataset.

### What I Learned

I learned that the original ResNet50 model predicts ImageNet categories, so its final classification layer must be replaced for our plant disease classes.

### How I Applied It

We modified the final ResNet50 layer, moved the model to the available CPU or GPU device, and configured the optimizer to train the new classification layer.

---

## 9. Building the Training and Validation Process

- **Date:** July 22, 2026
- **Tool Used:** ChatGPT

### Question Asked

> Can you help us write the PyTorch training and validation loops for the ResNet50 model?

### What the AI Suggested

ChatGPT suggested using training mode when updating the model weights and evaluation mode during validation. It also recommended tracking loss and accuracy after every epoch.

### What I Learned

I learned that training requires forward propagation, loss calculation, backpropagation, and optimizer updates. Validation measures model performance without changing the model weights.

### How I Applied It

We added working training and validation loops that calculate epoch loss and accuracy and display the model's progress.

---

## 10. Adding Image Prediction and Confidence Scores

- **Date:** July 22, 2026
- **Tool Used:** ChatGPT

### Question Asked

> How can our notebook accept a leaf image and return the predicted disease label with a confidence score?

### What the AI Suggested

ChatGPT suggested applying the same resizing and normalization used during model training, running the processed image through ResNet50, using softmax to calculate class probabilities, and matching the highest probability with its class name.

### What I Learned

I learned that new images must use the same preprocessing steps as the training images. I also learned that softmax converts the model outputs into probability-based confidence scores.

### How I Applied It

We added a prediction function that processes an uploaded leaf image and returns the predicted plant condition and its confidence score.

---
