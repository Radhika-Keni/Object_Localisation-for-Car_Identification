# Object Detection for Car Identification


## Objective of this notebook
- The purpose of this notebook is to build a Deep learning based car identification model
- Details of the **problem statement**  , **data set** ,  **summary of the code/solution**  , **sample output/Prediction** from the program and **final result** of the project are listed in the sections to follow.

## Problem Statement 
Computer Vision can be used to automate supervision and generate action appropriate action trigger  if the event is predicted from the image of interest.
In this particular use case, we will be exploring how a car moving on the road can be easily identified by a camera by identifying the make of the car, type, color, number plates, etc.This could be very useful for monitoring criminal activity, identifying fake license plates, etc. It could also be useful in several other use-cases like identifying popularity of certain car types/make in certain geographies etc


## Data Description:
- Data Set:Stanford Car Data Set hosted by Kaggle
- The Cars dataset contains 16,185 images of 196 classes of cars. The data is split into 8,144 training images and 8,041 testing images, where each class has been split roughly in a 50-50 split. Classes are typically at the level of Make, Model, Year, e.g. 2012 Tesla Model S or 2012 BMW M3 coup
- Train Images: Consists of real images of cars as per the make and year of the car. 
- Test Images: Consists of real images of cars as per the make and year of the car. 
- Train Annotation: Consists of bounding box region for training images. 
- Test Annotation: Consists of bounding box region for testing images

## Domain:
  Automotive Surveillance

## Summary of the Solution/Code:
The code aims at building a CNN model.
- We begin by doing an Exploratory Data analyses and Visualisation on the images , refer **python worksheet /EDA/EDA_And_Preprocessing.ipynb**
- We then do the required pre-processing for the data to make it compatible with the model to be built.We also perform the data splits because we will not be using 16,000  images due to hardware constraints , we will perform a Train Data Split Size=6500 Records and Validation Data Split Size=1629 Records
- We then move on to Model building which will be a simple keras classifier model that has been converted to an object detector. Essentially it is a convolution neural network(in this case with a  base skeleton of MobileNet)which is pre-trained on a ImageNet DataSet who’s top layer have been replaced by two heads , namely a regression head and a classification head. This can be thought of as two parallel networks , one which does classification and the other that calculates the bounding box , each having its own loss function respectively. The combined loss of these functions is what the network strives to reduce with each epoch during the training.
- -We also perform Hyper parameter tuning which involves going through multiple iterations while building the model to try different options for parameters such as  base skeleton n/w, top layers, optimizer and  image size
- The best model resulting from the above iterative process is chosen as the model refer **python worksheet /Custom Baseline Model/Final_Custom_Baseline_Model.ipynb**


## Sample Ouput/Prediction :
Here is a sample Ouput image to the program/model alongside the ground truth

![image](https://user-images.githubusercontent.com/68383273/191107674-7ea077b3-cb37-499e-bfd7-ad964f81a668.png)

## Result
- This model was able to obtain an accuracy of 0.70, IOU of 0.82 and mAp score of 0.592 .Refer **python worksheet /Custom Baseline Model/Calculate_mAp.ipynb** for mAp score calculation
