# Pets-Classification
Deep Learning Image Classifcation, CNN model
Pet Classification Using CNN Model
project write-up, by Miles He

The goal of the project is to study the impact of change in hyperparameters on the resulted accuracy and loss value for image classification in a Tensorflow and Keras Deep Learning CNN model.
The images are photos of cats and dogs, downloaded from the internet. They are pre-separated into 2 folders, under a folder named “train”. We use those images to train the program to classify those 2 genres of pets. So, this is a binary classification problem. 
We will finetune 3 parameters in the project: 
1.	Number of epochs – set to 100, 200, and 300 
2.	L2 regularization function in the convolution layer – with and without
3.	Number of images trained – 40 and 108
Our testing parameters are accuracy and loss.

Step 1: set the activation function in the output layer to softmax, instead of sigmoid. 
The result of this is a constant value for the accuracy which always equals to 0.5, for both training and validation. Change the number of epochs will not change this result. 

Step 2: change the activation function in the output layer to sigmoid. Number of trained images is 40, without L2 regularization function. Change number of epochs from 100, 200, to 300. 
	100	200	300
Accuracy training	0.625	0.800	0.875
Accuracy validation	0.558	0.600	0.650
Loss training	0.627	0..497	0.216
Loss validation	0.700	0.599	1.174

Conclusions: increasing the number of epoch while keep the other parameters the same shows an increase in the accuracy, in both training and validation (testing). Although the loss in training also decreases, the spread of loss between training and validation widens, suggesting a mild degree of overfitting issue when the number of epochs increases.
 
Step 3: increase the number of images for training, from 40 to 108, then repeat step 2. 
	100	200	300
Accuracy training	0.619	0.8	0.876
Accuracy validation	0.35	0.7	0.55
Loss training	0.649	0.43	0.263
Loss validation	0.747	1.434	2.373

Conclusions: increase the number of trained images in this case didn’t show improvement in the accuracy. Some of the accuracy in validation even fell. But the spread for both accuracy and loss between train and test widened, suggesting a significant overfitting problem. 

Step 4: Add the L2 regularization function into each convolution layer. Number of trained images is 108. Repeat step 2. 
	100	200	300
Accuracy training	0.722	0.438	0.780
Accuracy validation	0.650	0.60	0.650
Loss training	0.609	0.703	0.508
Loss validation	0.828	0.678	0.567

Conclusion: after adding the L2 regularization function, the gap between training and validation loss is significantly reduced, suggesting the overfitting issue is fixed. In terms of performance, the 300-epoch trail showed the highest accuracy and lowest loss value.

Other observations: 
Most of the trained image files are of size below 10k. I tried to add some large size images into the group, for example, a 2m bits cat image was loaded into the folder, to find out if the model works better using images containing larger information volume. The result for accuracy varies. For example, when the large size image for cat was added, the training accuracy seemed improved, reaching above 0.9, but testing accuracy was still around 0.68. Loss value for validation is dropped below 1. 
When further added a large size dog image into the trained group, result didn’t improve this time, it actually worsened – the spread of loss between training and validation was getting bigger. 
Therefore, whether size of images matters on the result is still up to more tests. 
 
