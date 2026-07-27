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
- **Tool Used**: ChatGPT
- **Question Asked**:  
  "How can a plant disease detection model distinguish between actual disease symptoms and natural leaf patterns, insect damage, or lighting effects?"

- **What the AI Suggested**:  
  A plant disease model can improve by training on diverse images, including healthy leaves, insect damage, natural spots, shadows, and different lighting. It can also use confidence scores or an “unknown” option when the image does not match any trained class.


- **What I Learned**:  
I learned that a plant disease model can confuse natural spots, insect damage, shadows, or lighting changes with disease symptoms. Diverse training images are important for improving real-world accuracy.

**How I Applied It:**
We tested our model with a healthy polka dot Begonia and used the incorrect prediction as a failure case. We also identified adding more real-world images and an “unknown” option as possible future improvements.

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

## 6. Identifying the Lowest-Performing Classes

* **Date**: July 22, 2026

* **Tool Used**: ChatGPT

* **Question Asked**:
  "How can we identify the lowest-performing PlantVillage classes from the classification report?"

* **AI Suggestion**:
  ChatGPT suggested reviewing the precision, recall, F1-score, and support for all 38 classes and sorting the classes by F1-score from lowest to highest. It also recommended checking the confusion matrix to determine which plant-disease classes are most often confused with one another.

* **What I Learned**:
  I learned that overall accuracy does not show how well the model performs on every class. A class with a low F1-score may have weak precision, weak recall, or both, so the per-class results are necessary for identifying specific weaknesses.

* **How I Applied It**:
  We used the classification report to focus on the classes with the lowest F1-scores and reviewed their precision, recall, support, and confusion patterns before suggesting model improvements.

---

## 7. Using a Working PlantVillage Dataset Mirror

* **Date**: July 22, 2026

* **Tool Used**: ChatGPT

* **Question Asked**:
  "Why did the original PlantVillage dataset fail to load in Colab, and how can we use a working dataset mirror?"

* **AI Suggestion**:
  ChatGPT explained that a dataset may fail to load in Colab when the source is unavailable, its download path or permissions have changed, or its file structure is incompatible with the loading code. It suggested using an accessible mirror that preserves the PlantVillage class folders, then verifying the class names, image counts, and directory structure before training.

* **What I Learned**:
  I learned that a failed dataset source does not necessarily mean the model code is incorrect. A dataset mirror can be used when it contains the same required images and labels, but the replacement source should be checked carefully for completeness and consistency.

* **How I Applied It**:
  We replaced the unavailable dataset source with a working PlantVillage mirror and confirmed that Colab could read the class folders and prepare the images for the 38-class classification model.

---

## 8. Comparing Macro and Weighted F1-Scores

* **Date**: July 22, 2026

* **Tool Used**: ChatGPT

* **Question Asked**:
  "What is the difference between macro F1-score and weighted F1-score for our 38-class model?"

* **AI Suggestion**:
  ChatGPT explained that macro F1 calculates the F1-score for each class and gives all 38 classes equal importance when averaging. Weighted F1 also averages the class F1-scores, but it gives more influence to classes with more test images.

* **What I Learned**:
  I learned that macro F1 is useful for determining whether the model performs consistently across all classes, especially smaller classes. Weighted F1 reflects performance according to class frequency and can remain high even when some less common classes perform poorly.

* **How I Applied It**:
  We reported macro F1 as an important project metric and compared it with weighted F1 and the per-class classification report to avoid judging the model only by overall accuracy.

---

## 9. Improving Performance on Unfamiliar Plants

* **Date**: July 22, 2026

* **Tool Used**: ChatGPT

* **Question Asked**:
  "How could we improve the model’s performance on unfamiliar plants without changing the 38 PlantVillage output classes?"

* **AI Suggestion**:
  ChatGPT suggested improving generalization by using more varied training images, stronger but realistic augmentation, field-style backgrounds, different lighting conditions, and fine-tuning with additional examples that still belong to the existing 38 classes. It also suggested using confidence thresholds to warn users when a prediction may be unreliable.

* **What I Learned**:
  I learned that the model can become more robust without adding output classes by increasing the visual variety within the existing classes. However, a plant or disease outside the 38 trained classes cannot be reliably identified as a new category by the current classifier.

* **How I Applied It**:
  We identified realistic augmentation, more diverse images, additional fine-tuning, and low-confidence warnings as possible future improvements while keeping the model’s output layer fixed at 38 classes.

---

## 10. Understanding the Effect of Class Imbalance

* **Date**: July 22, 2026

* **Tool Used**: ChatGPT

* **Question Asked**:
  "How could class imbalance affect the model’s predictions?"

* **AI Suggestion**:
  ChatGPT explained that classes with many training images can influence the model more strongly than classes with fewer images. This may cause the model to predict common classes more often and produce lower recall or F1-scores for underrepresented classes.

* **What I Learned**:
  I learned that a model can have high overall accuracy while still performing poorly on minority classes. Per-class metrics and macro F1 are important for detecting this problem.

* **How I Applied It**:
  We reviewed the number of images in each class and considered class-weighted loss, balanced sampling, targeted augmentation, and per-class evaluation as possible ways to reduce the effect of imbalance.

---


---
