## About

In this repository, I created a tf.keras.Sequential model and trained it on a random generated data set. Ultimately, the goal of this model is to tell us whether or not a patient will experience side effects solely based on the patient's age.

## Prerequisite
Before you get to work on this project, it's recommended that you have a relevant environment.
In this case, I used Anaconda to set up the environment.(*Consider installing Anaconda  if you haven't had it installed already*)
Secondly, Jupyter Notebook or Colab Notebook are just great if used. However, you can still use an IDE of your choice.

### Set-Up and Pre-installation Guide
With Anaconda installed we'll need to set up our environment in our desired directory on the local machine using the command below on the terminal or cmd (*This environment will have tensorflow for CPU intalled in it*):

- `conda create -n <environment name> tensorflow`

Once created, activate it using:

- `conda activate <environment name>`

With the conda environment activated, install this libraries and packages  using the  commands below.
- `conda install numpy`
- `conda install scikit-learn`
 

At  this point we can serve to the our Jupyter Notebook and and get our hands at work
Serving the Jupyter notebook from the terminal is quite easy if you have it installed; just run thi command:
- `jupyter-notebook`
 

**Note: *If at all you did follow this guide, we just created an environment with Tensorflow for CPU already installed in it. Keras package which we will be using for developing our model, is fully integrated with the Tensorflow package***

## Data Creation 
**Creating our own example data set.**
As a motivation for this data, let's assume that an experimental drug was tested on  individuals ranging from age 13 to 100 in a clinical trial. The trial had 2100 participants. Half of the participants were under 65 years old, and the other half was 65 of age or older.

Below is a snippet for the data created. 
![images.jpeg](images/model_data.jpeg)

### Data processing
We created a list containing 2100 total items and their corresponding labels (either 0 or 1 to represent those who didn't experience side effects  and those who did experience respectively). This is supervised model. It will use its knowledge gained from training and using it to infer a prediction or result.

We converted the list to  a numpy array which we then scaled to a scale of 0 to 1 using scikit-learn's MinMaxScaler class.


For this model, I created three sets of data
- **Traing Data** ---> To be used for training the model.
- **Validation Data** ---> For validation purpose.
- **Test Data** --->  It will be used without labels to test the accuracy of the already trained model in predicting results  
Check out the notebook file containing this code in this repo  named **ModelTrain_Data.ipynb** 

## Building our sequential model 
**Goal of this model** ---> Ultimately our model should tell us whether or not a patient will experience side effects solely based on the patient's age.


Check out the notebook file containing the code for this  model in this repo named **Neural_Network_Model.ipynb**
We  first instantiate  the Sequential object which is a linear stack of layers. We then  passed in a list of layers to the Sequential constructor. In this case, all the layers were dense layers.

Here is a snippet of what the model code looks like 
![images.jpeg](images/built_model.jpeg)

After creation of the model we train it on the data that we generated earlier (Both the validation and training data)
In our case we used an Epoch size of 30 during training. You can increase the epoch size of your model for better  accuracy.

After training, the model was tested on a separate **Test data** which was passed without labels so the model would predict on the data and let us Know if one experienced side effects or not.

## Confusion matrix 
We created a confusion matrix which aided us in being able to visually observe how well was the  neural network model predicting during inference. 
Here is the confusion matrix result
![images.jpeg](images/confusion_matrix.jpeg)

#### Reading the confusion matrix
Looking at the plot of the confusion matrix, we have the predicted labels on the x-axis and the true labels on the y-axis. The blue cells running from the top left to bottom right contain the number of samples that the model accurately predicted. The white cells contain the number of samples that were incorrectly predicted.

There are 420 total samples in the test set. Looking at the confusion matrix, we can see that the model accurately predicted 396 out of 420 total samples. The model incorrectly predicted 24 out of the 420.

## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)