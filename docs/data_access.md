# Data access and handling

## Dataset

This project uses the official **GLENDA v1.0** laparoscopic image dataset. The repository does not include the dataset, derived image files, annotation masks, or model checkpoints.

## Obtaining the data

Download GLENDA only from its official distribution channel and comply with its license, citation requirements, and any applicable institutional conditions. The end-to-end notebook contains the download and extraction workflow used for the study.

## Derived targets

For pathology images, all official lesion-instance masks corresponding to an image are merged into a single binary lesion mask. No-pathology images receive an all-zero mask. This creates a consistent target for binary semantic segmentation while preserving the original image-level pathology label.

## Repository policy

Do not commit any of the following:

- Original or derived GLENDA images and annotations.
- Download archives or extraction directories.
- Google Drive caches, intermediate files, or experiment outputs.
- Model checkpoints or third-party pretrained weights.
- Access tokens, credentials, or personal paths.

The `.gitignore` file enforces these exclusions for the common cases. Review staged changes before every commit.
