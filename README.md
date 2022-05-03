# Project X-ray (UNIFESP Kaggel Competition)

## Introduction ##

This notebook proposes a solution to the competition posted by UNIFESP at Kaggle.com on the 20th of March 2022, entitled "UNIFESP X-ray Body Part Classifier Competition".<br/>
The objective was to classify DICOM X-ray images by body anatomy segment. More detailed explanation can be found on the website bellow, under "Overview".<br>
Link: https://www.kaggle.com/competitions/unifesp-x-ray-body-part-classifier


## Data ##
Source: API provided by competition host, 'kaggle competitions download -c unifesp-x-ray-body-part-classifier'

## Technology ##
Python 3.9.7

## Libraries ##
* pandas
* numpy
* matplotlib
* seaborn
* pydicom
* sklearn
* skimage
* pathlib

## DataFrame ##
Two .csv files ("train.csv" and "sample_submission.csv") were available for downloading.<br/>
The "train.csv" file carries two columns of objects, with an image ID as "SOPInstanceUID" and the represented body anatomy segment as "Target". This file was used to generate samples for the purpose of the coding.<br/>

A decorticated and labeled dataframe was created to facilitate visualisation.<br/>
![image](https://user-images.githubusercontent.com/92320460/165941340-8e648785-c9de-490a-8e41-124fe29c5072.png)

The next step was to aggregate the image files' path to the correct "SOPInstanceUID" in the dataframe refering to the DICOM metadata.<br/>
![image](https://user-images.githubusercontent.com/92320460/166117032-c985a3a6-0dc4-484d-8bdd-3f5ed4992d71.png)

## Images ##
Two sets of images in DICOM (https://www.dicomstandard.org/) format were availabe:
* train: 1738 images
* test: 743 images

The "train" images were used splitted to train and test the models.<br/>
The "test" images were used to generate a validation ".csv" file, which was submited as our solution for the competition.<br/>

As a first implementation, The DICOM images were decoded into matrices and subsequently:
- resized (1000 x 1000);
- transformed into a vector with a 1e6 elements;
- standardized;
- decomposed/tranformed (PCA)

### 1. PCA ###

Bellow, the cumulative values curve and an example of an iamge recomposed after PCA transformation with 5, 10 and 50 elements:<br/>
![image](https://user-images.githubusercontent.com/92320460/166394720-542f842f-54d1-4b31-a06f-7fe29fe5fb0c.png)

Two other transformation/compression technics were tested as well:<br/>

### 2. Hiastogram of Oriented Gradient (HOG) ###
![image](https://user-images.githubusercontent.com/92320460/165867625-3b2acd9c-ef05-44b0-9b8f-26cac8f5d790.png)

### 3. Singular Value Decomposition (SVD) ###
<img width="693" alt="image" src="https://user-images.githubusercontent.com/92320460/166395015-263d8ce1-13c7-4037-96e8-06954158c466.png">

![image](https://user-images.githubusercontent.com/92320460/166395133-ac476fa7-c891-4735-8673-c6fc9151e2be.png)

## Calssificaiton Models ##
* Catboost
* Stochastic Gradient Descent (SGD)

In a preliminary result with 2 categories (labels), knee and wrist, similar results where obtained, with F1 scores of 0.812.<br/>
Below, an example showing the original image and the reconstructed one from the PCA data resulted from the models:

<img width="387" alt="image" src="https://user-images.githubusercontent.com/92320460/166396161-ea1bd957-ba88-4336-b438-74b289c3746d.png">

However, the models showed low score as the number fo categories increased(e.g 6 categopries F1 score = 0.35.

## Next Steps ##
* Optimize image transformation
* apply different image transformation to the models
* Model parameters optimization

## Author ##
* Sergio G. Pasian: https://github.com/SGPracing

## Acknowledgements ##
Special thanks to Pedro Teche and Adriano Yoshizawa, not only for the immense support and contribution to this project, but for all their dedication, sharing their knowledge with patience and wisdom throughout my training.

