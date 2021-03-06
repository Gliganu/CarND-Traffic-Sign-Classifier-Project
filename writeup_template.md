# **Traffic Sign Recognition** 

## Writeup

### You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/counts.png "Visualization"
[image3]: ./examples/random_noise.jpg "Random Noise"
[image4]: ./examples/pic-1.jpeg "Traffic Sign 1"
[image5]: ./examples/pic-2.jpeg "Traffic Sign 2"
[image6]: ./examples/pic-3.jpeg "Traffic Sign 3"
[image7]: ./examples/pic-4.jpeg "Traffic Sign 4"
[image8]: ./examples/pic-5.png "Traffic Sign 5"

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my [project code](https://github.com/Gliganu/CarND-Traffic-Sign-Classifier-Project)

### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of the validation set is 4410
* The size of test set is 12630
* The shape of a traffic sign image is 32,32
* The number of unique classes/labels in the data set is 43

#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data ...

![alt text][image1]

### Design and Test a Model Architecture

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)

I normalized the image data in order to bring all the data to the same scale. In order to normalize the data I substracted the mean and divided by the standard deviation

#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the classic LeNet-5 architecture, but with 3 color channels instead of just one.

| Layer			        |     Input shape |  Output shape  |
|:---------------------:|:---------------:|:--------------:|
| Conv2D                | 32x32x1   	  | 28x28x6        |
| Max Pooling           | 28x28x6         | 14x14x6        |
| Conv2D                | 14x14x6         | 10x10x16       |
| Max Pooling		    | 10x10x16        | 5x5x16         |
| Flatten               | 5x5x16          | 400            |
| Fully Connected       | 400             | 120            |
| Fully Connected       | 120             | 84             |
| Fully Connected       | 84              | 10             |

#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an Adam optimizer with a batch size of 128. I trained the network for 100 epochs with a learning rate of 0.0005

#### 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* training set accuracy of 0.974
* validation set accuracy of 0.941

#What architecture was chosen?
I chose the LeNet5 architecture, but with 3 color channls instead of just 1.

#Why did you believe it would be relevant to the traffic sign application?
Because it has been proved to perform quite well on relatively easy image-classification tasks, such as MNIST and this task resembles MNIST in a lot of ways, such as the fact the images are quite small and simple. 

#How does the final model's accuracy on the training, validation and test set provide evidence that the model is working well?
As the model has reached accuracies of above 93% both on the test and on the validation sets, it has proven able to classify the traffic signs in a wide majority of cases.

### Test a Model on New Images

#### 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

![alt text][image4] ![alt text][image5] ![alt text][image6] 
![alt text][image7] ![alt text][image8]

A list of reasons why the new images could be difficult to classify include but are not restricted to:

- Different lighting / orientations than those from the training set

- The cropping around the sign is bigger / smaller than the one in the dataset

- The sign could not be located in the center of the image

#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| No entry      		| No entry   									| 
| Stop      			| Speed limit 30                                |
| Turn right ahead		| Turn right ahead                              |
| Yield	      		    | Speed limit 50                                |
| Roundabout mandatory  | Roundabout mandatory                          |


The model was able to correctly guess 3 of the 5 traffic signs

#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the 11th cell of the Ipython notebook.

For the first image, the model is relatively sure that this is a stop sign (probability of 0.6), and the image does contain a stop sign. The top five soft max probabilities were

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .33        			| No entry   									| 
| .24     				| Bicycles crossing                             |
| .17					| No passing									|

 