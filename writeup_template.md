# **Behavioral Cloning** 

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./center.png
[image2]: ./center2.png
[image3]: ./center3.png

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/432/view) individually and describe how I addressed each point in my implementation.  

---
### Files Submitted & Code Quality

#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode

My project includes the following files:
* model.py containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md or writeup_report.pdf summarizing the results
* final.mp4 video of the first track trained model trial.

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```

#### 3. Submission code is usable and readable

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

First i preprocess the data, then train the network.

The network consists of :
1. Normalization layer (preprocess)
2. Cropping layer. Crop the images from the upper and lower part of the images to help the model train faster (preprocess)
3. Convolution layer -with filter size = 32- followed by a relu activation.
4. Max pooling layer with filter size of 2x2.
5. Convolution layer -with filter size = 48- followed by a relu activation.
6. Max pooling layer with filter size of 2x2.
7. Convolution layer -with filter size = 64- followed by a relu activation.
8. Max pooling layer with filter size of 2x2.
9. flatten the array to 1-D array to process it with a fully connected network.
10. hidden layer with 128 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
11. hidden layer with 64 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
12. hidden layer with 32 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
13. the output neuron for the steering angle.

#### 2. Attempts to reduce overfitting in the model

The model contains dropout layers in order to reduce overfitting. 

The model was trained and validated on different data sets to ensure that the model was not overfitting . The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually.

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving, recovering from the left and right sides of the road in both directions. 

### Model Architecture and Training Strategy

#### 1. Solution Design Approach

The overall strategy for deriving a model architecture was to drive for several laps in both directions (clockwise and counter clock wise)

In order to gauge how well the model was working, I split my image and steering angle data into a training and validation set. I found that my first model had a low mean squared error on the training set but a high mean squared error on the validation set. This implied that the model was overfitting. By some tuning to the network size and parameters it worked. 

The final step was to run the simulator to see how well the car was driving around track one. 

At the end of the process, the vehicle is able to drive autonomously around the track without leaving the road.

#### 2. Final Model Architecture

The final model architecture consisted of a :
1. Normalization layer
2. Cropping layer. Crop the images from the upper and lower part of the images to help the model train faster
3. Convolution layer -with filter size = 32- followed by a relu activation
4. Max pooling layer with filter size of 2x2.
5. Convolution layer -with filter size = 48- followed by a relu activation
6. Max pooling layer with filter size of 2x2.
7. Convolution layer -with filter size = 64- followed by a relu activation
8. Max pooling layer with filter size of 2x2.
9. flatten the array to 1-D array to process it with a fully connected network.
10. hidden layer with 128 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
11. hidden layer with 64 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
12. hidden layer with 32 hidden neuron followed by a relu activation and dropout with keep_prob = 50%.
13. the output neuron for the steering angle.


#### 3. Creation of the Training Set & Training Process

To capture good driving behavior, I first recorded two laps on track one using center lane driving. Here is an example image of center lane driving:

![alt text][image1]

I then recorded the vehicle recovering from the left side and right sides of the road back to center so that the vehicle would learn to .... These images show what a recovery looks like starting from ... :

![alt text][image2]
![alt text][image3]

Then I repeated this process several times in order to get more data points.

After the collection process, I had around 10,100 number of data points. I then preprocessed this data by normalization and cropping.


I finally randomly shuffled the data set and put 20% of the data into a validation set. 

I used this training data for training the model. The validation set helped determine if the model was over or under fitting. The ideal number of epochs was 5 as evidenced by ... I used an adam optimizer so that manually training the learning rate wasn't necessary.
