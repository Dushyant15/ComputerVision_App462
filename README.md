# Classifying Images with Vision and Core ML

Preprocess photos using the Vision framework and classify them with a Core ML model.

## Overview

With the [Core ML](https://developer.apple.com/documentation/coreml) framework, you can use a trained machine learning model to classify input data. The [Vision](https://developer.apple.com/documentation/vision) framework works with Core ML to apply classification models to images, and to preprocess those images to make machine learning tasks easier and more reliable.

This app uses a CreateML trained HumanEmoClassfier_8.mlmodel model, that helps classify each face based on the emotion shown in to one of four categories (Angry, Disgust, Happy, Sad).

![example screenshots of the app identifying a happy, disgust and sad face](Documentation/Classes.png)

## Getting Started

This sample code project runs on iOS 11. However, you can also use Vision and Core ML in your own apps on macOS 10.13, iOS 11, or tvOS 11.

## Table of Contents
- [DataSet](#dataSet)
- [Using CreateML to train a Image Classification model](#Using_CreateML_to_train_a_CNN_Model)
- [Export the trained model](#Export_the_trained_model)
- [Add the model to Xcode project](#Add_the_model_to_a_Xcode_Project)
- [Make Changes to Xcode project, build and execute](#Xcode_update_build_execute)
- [Other commands that you might need](#Other_commands_that_you_might_need)

## DataSet
  > Where I get the Image data for four Human Emotions (Happy, Sad, Disgust & Angry) ?  
    I scrapped the images using the bing_scraper.py (attached)   
  
    You can execute the script using the following command:
    python3 bing_scraper.py --search 'happy human face' --limit 10 --download --chromedriver /Users/dushyantsengar/documents/docs/chromedriver
    
    To be able to successfully run above script, please download the chromedriver. Then, place the .py script in the same folder and CD to same directory on the terminal. Execute the script by the changing the query in the single quotes and number of images you need to download.
            
## Using_CreateML_to_train_a_CNN_Model

  >(1) How do I upload the training and test pictures and train the module using CreateML?  

## Export_the_trained_model
  >(2) How do I copy the trained model to the local dir for further deployment / integration with the iOS app ?
    
    You can watch my youtube video that describes the steps to accomplish above mentioned two steps:  
          
   [Train an Image Classifier using CreateML] (https://www.youtube.com/watch?v=M58_XOyJW04&feature=youtu.be).
             
   
## Add_the_model_to_a_Xcode_Project 

   > Use the trained and downloaded model for iOS app deployment?
   
        It can be done in following four steps: 

   >(1) Download the pre-built sample app that uses Vision to apply the Core ML model to the chosen image, and shows the resulting classification labels along           with numbers indicating the confidence level of each classification. 
        It displays the top two classifications in order of the confidence score the model assigns to each.  
       
        Link to download the app:
        
        https://developer.apple.com/documentation/vision/classifying_images_with_vision_and_core_ml 
     
     
   >(2) Open the Xcode project and Understand the Swift Architecture for making inference/predictions
    
       1) Create one or more requests. This step should have created a request using a .MLMODEL object.This is done by the "classificationRequest" function
       2) Create and run a request completion handler. 
          This handler is responsible for invoking the actual classification task (using "processClassifications") and prints the output of classification.
       3) Also create a separate handler to perform the Asynchronous Vision request, and then schedule that request. 
          This is done by the "updateClassifications" function by invoking the previously created request by the "classificationRequest" function
       4) Finally, adding the imagePickerController(_:didFinishPickingMediaWithInfo:): updateClassifications(image) at the end of the Swift code
          will trigger the classification request when the user selects an image.
        
        
   >(3) Add the trained CreateML module to the Xcode project that would generate a Swift class 
    
        Please refer to the linked Youtube video. This is largely a drag and drop and excercise.
        
   >(4) Add a simulator or an iPhone device to output your model output
    
        Please refer to the linked Youtube video. 
        These are pre-built in the Xcode environment. You need to register a team using your AppleID to be able to use all features of Xcode environment. 
        One can also register their iPhone as a simulator to take real time pictures and classify.
   
   You can watch my youtube video that describes the steps to accomplish above mentioned four steps:  
          
   [Build an iOS app using the trained CreateML model](https://www.youtube.com/watch?v=nJc4DEusYbU&feature=youtu.be).
        
## Xcode_update_build_execute 
  In this section, we would list out sections on the Xcode that need to be set up before build and execute can happen succesfully
    
    >(1) Set up the unique Build Identifier and Create a Team (personal team using AppleID) to be able to build and execute a project
    
        
    >(2) Setting up the right version as per the model file 
    
      
## Other_commands_that_you_might_need

   
  1. GitHub Upload
     - Create a new repository in Github
     - Open a terminal on the local project folder by right clicking on the folder
      
  2. Then perform the following steps on the terminal
     - git init : This initializes the local git repository
     - git add . 
     - git commit -m "my first commit"
     - git remote add origin https://github.com/Dushyant15/ComputerVision_App462.git : This connects your local git to online newly created repository
     - git push -u origin master : This pushes the local files to the github repository
      
