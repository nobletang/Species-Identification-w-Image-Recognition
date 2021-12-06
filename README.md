# Introduction

In this journal, a machine learning model is used to identify flowers through image classification. This multi-classification model is trained with thousands of images which are randomly augmented to achieve better generalization. The model serves to be a proof of concept in battling invasive plant species that damages the fragile ecosystem it resides in. The journal will contain the steps taken to arrive to a similar model. Analysis of the results will be mentioned in the later sections, followed by what the results mean for the stakeholder.

# Business Understanding

Every year, the U.S. is estimated to lose $120B due to the impact of invasive plant species. Invasive plant species can reduce yield in nearby agriculture, kill existing plants, increase the risk of forest fires, and much more. While the spread of invasive plant species can be slowed at the airport, the plants that reside in America right now need to be found and removed. Programs to remove these plants are already in place, but can be accelerated through the use of machine learning and scouting tools like drones. Drones can quickly scout dangerous terrain and machine learning can quickly review photos to identify an invasive plant species. This proposal will help reduce cost spent in manual labor and remove the risk of workers traversing dangerous terrain.

# Data Understanding

* what data are we working with
* how many images are we working with
* how are the images separated
* what are in the images? what useless info is included? what useful info is included?
* how the images prepared?

There are 104 different flower species provided in this dataset. There are 16,463 images provided in the dataset and each image are of flowers with different compositions. An image can be of a distant rose bush, a macro photo of a sunflower bud, or a hibiscus tucked behind the ear. The distribution of these flowers are not equal and would result in some preprocessing before models should be trained.

**perhaps a visualization of the distribution here**

# Data Preparation

The structure of the directory has class labels for the train and validation folder, but the test folder contains images without any labels. To create a typical train, validate, and test structure, the images in the test folder will be ignored from this point on. 10% of the images found in the train folder will be moved into a new test folder. The result are three folders with labeled classes.

With this directory set up, we can now remove the classes of flowers that do not have enough information to train a model on. Functions have been created to select these folders to avoid manually separating the folders by hand. In the models shown in the notebook, the 10th percentile of the number of images found in the training are removed from the scope. This leaves 96 classes with 16,268 images. On average, there should be 168 images per class that can be divided into train, validate, and test sets. 

Because there are not enough images to properly train a model with nearly 100 classes, data augmentation will be used to make the model more generalizable. Each image will randomly flip, change in brightness, crop, and many other transformations. Also, with these images being RGB, the images will need to be standardized and represented in the range of 0 and 1.

# Modeling

Through many iterations, the final model came out to be a convolutional neural network (CNN) with several layers. The model would look through each image and run for 20 epochs. There is also a learning rate that will reduce the rate at which the model will train. The goal of the learning rate is to keep training loss to not get too ahead of the validation loss.

There are some attempts at improving the model during training but metrics were not improving. The model faced much overfitting issues but the model does not use BatchNormalization and Dropout layers. Adding these layers did not help improve the validation accuracy metric. When attempting to introduce transfer learning, the results instead reduced the validation accuracy metric and increased validation loss. With shorter run times and better metrics, these layers were left from the final model.

# Analysis

* what results do we get
* what do those results mean
* how can we improve on this result
* does the result work in favor of the business problem



# Conclusion

* what have we done
* what have we learned
* what can the model do for the business problem


```python

```
