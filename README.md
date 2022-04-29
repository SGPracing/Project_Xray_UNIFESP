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
### .csv files ###
Two.csv files ("train.csv" and "sample_submission.csv") were available for downloading.<br/>
The "train.csv" file carries two columns of objects, with an image ID as "SOPInstanceUID" and the represented body anatomy segment as "Target". This file was used to generate samples for the purpose of the coding.<br/>

A decorticated and labeled dataframe was created to facilitate visualisation.<br/>

### Images ###
Two sets of images in DICOM (https://www.dicomstandard.org/) format were availabe:
* train: 1738 images
* test: 743 images

The "train" images were used splitted to train and test the models.<br/>
The "test" images were used to generate a validation ".csv" file, which was submited as our solution for the competition.<br/>

#### Image treatment ####
The DICOM images were decoded into matrices and subsequently:
- resized (1000 x 1000);
- transformed into a vector with a 1e6 elements;
- standardized;
- decomposed using PCA

This is an example


