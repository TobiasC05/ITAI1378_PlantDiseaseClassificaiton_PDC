# Pixel Predators Results

This folder contains final evidence for the 38-class ResNet50 plant
disease classification project.

## Included Files

- `metrics_summary.csv`
- `per_class_f1_summary.csv`
- `lowest_performing_classes.csv`
- `metrics_vs_targets.png`
- `lowest_performing_classes.png`
- `correct_healthy_prediction.png`
- `begonia_failure_prediction.png`
- `prediction_examples.md`

## Main Results

- Test accuracy: 97.71%
- Macro F1-score: 0.9773
- Weighted F1-score: 0.9770
- Test images: 3,269
- Lowest-performing class: Tomato Early Blight
- Lowest class F1-score: 0.8984

## Important Note

A confusion matrix and training-history graph are not included here
because the raw prediction arrays and epoch-by-epoch history were not
available in the saved notebook file. Those files should only be
exported from the actual completed Colab run, not recreated from guessed
values.
