# Melanoma-Skin-Cancer-Pred

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Data](#data)
  * [Frameworks used](#frameworks-used)
  * [Labels](#labels)
  * [Evaluation Metric](#evaluation-metric)
  * [Cross-Validation](#cross-validation)
  * [Data-Augmentations](#data-augmentations)
  * [Result](#result)

## Overview
This is a simple image classification Project trained on the top of Pytorch API. The trained model that takes Skin Lesion Images as an input and predict the class of image from {'Benign Melanoma Cancer', 'Malignant Melanoma Cancer'}

## Motivation
Skin cancer is the most prevalent type of cancer. Melanoma, specifically, is responsible for 75% of skin cancer deaths, despite being the least common skin cancer. The American Cancer Society estimates over 100,000 new melanoma cases will be diagnosed in 2020. It's also expected that almost 7,000 people will die from the disease. As with other cancers, early and accurate detection—potentially aided by data science—can make treatment more effective.

Currently, dermatologists evaluate every one of a patient's moles to identify outlier lesions or “ugly ducklings” that are most likely to be melanoma. Existing AI approaches have not adequately considered this clinical frame of reference. Dermatologists could enhance their diagnostic accuracy if detection algorithms take into account “contextual” images within the same patient to determine which images represent a melanoma. If successful, classifiers would be more accurate and could better support dermatological clinic work.

## Data
The dataset was generated by the International Skin Imaging Collaboration (ISIC) and images are from the following sources: Hospital Clínic de Barcelona, Medical University of Vienna, Memorial Sloan Kettering Cancer Center, Melanoma Institute Australia, The University of Queensland, and the University of Athens Medical School.

The dataset contains 33126 skin lesion images.
To download the dataset images go to the following link or use the following command
``` kaggle competitions download -c siim-isic-melanoma-classification ```

The data can be found in the folder (`input/train_images/train_images.csv`)

## Frameworks-used
1. Pillow
2. OpenCV
3. Pandas
4. scikit-learn
5. Pytorch
6. Albumentations


![](https://forthebadge.com/images/badges/made-with-python.svg)

## Labels
{0: 'Benign Melanoma Cancer',
 1: 'Malignant Melanoma Cancer'}
 
 ## Evaluation Metric

The Data distribution is very skewed:
label 0: 32,542
label 1: 584

As you can see that the label 0 is about 56 times the label 1

Thus Accuracy would be a very very bad metric here, given the huge imbalance, We are going to Validate our model using "AUC ROC".

## Cross-Validation
We are going to use Stratified K Fold cross-validation method, because there is high class imbalance in the dataset. We are using 5 folds.

## Model

We are using CNN based model with the efficient-net-b4 architecture for the classification of the Skin Lesion Images.

## Data-Augmentations
**train dataset transformations**
        1. RandomResizedCrop
        2. Transpose
        3. HorizontalFlip
        4.VerticalFlip
        5. ShiftScaleRotate
        6. HueSaturationValue
        7. RandomBrightnessContrast
        8. Normalize
        9. CoarseDropout
        10. Cutout

**valid dataset transformations**
        1. CenterCrop
        2. Resize
        3. Normalize

## Result

* We get an AUC-ROC Score of 0.905
