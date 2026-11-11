# Reproducibility protocol

## Split integrity

The study uses five-fold grouped cross-validation with `video_id` as the grouping variable. Every frame from a given video is assigned to one and only one held-out fold. Thus, no frame from a held-out video is used for training in that fold.

The fixed manifests must be created before model training and retained unchanged for all models and analyses. The classifier and U-Net use the same fold assignment so their localization results can be compared fairly on identical held-out images and videos.

## Model selection

For each fold, the classifier checkpoint is selected using validation ROC-AUC. The segmentation checkpoint is selected using validation positive-image Dice. The held-out fold is not used to select model epochs or thresholds.

## Evaluation hierarchy

Each image is evaluated only by the model trained without its video. Out-of-fold image results are pooled only after all folds have completed. Video-level summaries aggregate held-out frames belonging to the same video.

## Explainability analysis

Classifier Grad-CAM maps are computed for held-out pathology images and compared with official lesion masks. Direct segmentation and Grad-CAM localization are compared at image and video levels. Faithfulness is assessed by measuring the change in pathology probability after blurring the official lesion region versus a matched non-lesion control region.

## Required saved artifacts

For each completed fold, retain the fixed manifests, experiment configuration, training history, latest checkpoint, selected best checkpoint, held-out predictions, metrics, and plots. These artifacts allow a run to resume after a Colab disconnection and make reported results traceable to their trained models.
