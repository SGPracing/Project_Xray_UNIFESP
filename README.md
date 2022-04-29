# Project X-ray (UNIFESP)

## 1. Introduction ##

This notebook proposes a solution to the competition posted by UNIFESP at Kaggle.com on the 20th of March 2022, entitled "UNIFESP X-ray Body Part Classifier Competition".<br/>
The objective was to classify DICOM X-ray images by body anatomy segment. More detailed explanation can be found on the website bellow, under "Overview".<br>
Link: https://www.kaggle.com/competitions/unifesp-x-ray-body-part-classifier


## 2. Data ##
Source: API provided by competition host, 'kaggle competitions download -c unifesp-x-ray-body-part-classifier'

## 3. Technology ##
Python 3.9.7

## 4. Libraries ##
* pandas
* numpy
* matplotlib
* seaborn
* pydicom
* sklearn
* skimage
* pathlib

## 5. DataFrame and Images##
### 5.1. ".csv" files ###
Two.csv files ("train.csv" and "sample_submission.csv") were available for downloading.<br/>
The "train.csv" file carries two columns of objects, with an image ID as "SOPInstanceUID" and the represented body anatomy segment as "Target". This file was used to generate samples for the purpose of the coding.<br/>

A decorticated and labeled dataframe was created to facilitate visualisation.<br/>

### 5.2. Images ###
Two sets of images in DICOM (https://www.dicomstandard.org/) format were availabe:
* train: 1738 images
* test: 743 images

The "train" images were used splitted to train and test the models.<br/>
The "test" images were used to generate a validation ".csv" file, which was submited as our solution for the competition.<br/>

The DICOM images were decoded into matrices and subsequently:
- resized (1000 x 1000);
- transformed into a vector with a 1e6 elements;
- standardized;
- decomposed/tranformed using PCA adn HOG

This is an example of an image, original format and processed as detailed above, using PCA with n_elements = 50:<br/>
![image](https://user-images.githubusercontent.com/92320460/165867472-f37f3948-ccd5-4721-8f6d-d1c8a3fa219f.png)

![image](https://user-images.githubusercontent.com/92320460/165867134-2dd862c1-22bb-4eeb-9722-4b128d177590.png)

This is the same image submitted to a HOG transformation:<br/>
![image](https://user-images.githubusercontent.com/92320460/165867625-3b2acd9c-ef05-44b0-9b8f-26cac8f5d790.png)








