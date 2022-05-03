# Project X-ray (UNIFESP)

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

## DataFrame and Images##
### 1. ".csv" files ###
Two .csv files ("train.csv" and "sample_submission.csv") were available for downloading.<br/>
The "train.csv" file carries two columns of objects, with an image ID as "SOPInstanceUID" and the represented body anatomy segment as "Target". This file was used to generate samples for the purpose of the coding.<br/>

A decorticated and labeled dataframe was created to facilitate visualisation.<br/>
![image](https://user-images.githubusercontent.com/92320460/165941340-8e648785-c9de-490a-8e41-124fe29c5072.png)

The next step was to aggregate the image files' path to the correct "SOPInstanceUID" in the dataframe refering to the DICOM metadata.<br/>

### 2. Images ###
Two sets of images in DICOM (https://www.dicomstandard.org/) format were availabe:
* train: 1738 images
* test: 743 images

The "train" images were used splitted to train and test the models.<br/>
The "test" images were used to generate a validation ".csv" file, which was submited as our solution for the competition.<br/>

The DICOM images were decoded into matrices and subsequently:
- resized (1000 x 1000);
- transformed into a vector with a 1e6 elements;
- standardized;
- decomposed/tranformed (PCA)

This is an example of an image, in the original format and transformed (PCA with n_elements = 50) as detailed above:<br/>
![image](https://user-images.githubusercontent.com/92320460/165962796-31969ce8-52dc-4e48-89c6-ce21ef6bf650.png)

![image](https://user-images.githubusercontent.com/92320460/165867134-2dd862c1-22bb-4eeb-9722-4b128d177590.png)

This is the same image submitted to a HOG transformation:<br/>
![image](https://user-images.githubusercontent.com/92320460/165867625-3b2acd9c-ef05-44b0-9b8f-26cac8f5d790.png)







![image](https://user-images.githubusercontent.com/92320460/166117032-c985a3a6-0dc4-484d-8bdd-3f5ed4992d71.png)

