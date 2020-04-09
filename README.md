# Image-Segmentation-Unet-DeepLabV3-Segnet

Semantic Segmentation models have been trained on the MoNuSeg Dataset comprising of 30 H&E stained tissue trainins Images of 30 patients with tumors of different organs. The dataset also has a subset of 14 images for validation of the models. The images were taken at 40 times magnification. 

https://monuseg.grand-challenge.org/Data/

Three architectures have been used for learning purposes:

* Segnet
* Unet 
* DeepLabV3

The implementation and results of each have been provided in their respective Jupyter notebooks in this repository.

The metrics that have been used are Loss, Accuracy, Dice Coefficient and F1-Score. The The best results have been obtained with the **Unet** which are listed below.
Test Results on Unet:
* Loss: 0.3436
* Accuracy: 91.40%
* Dice Coefficient: 0.7728
* F1-Score: 0.7889

Actual image size is 1000x1000 but for training purposes patching of 256x256 has been implemented. The settings for Unet that were used are given below:
* Optimizer = Adam
* Initial Learning Rate = 0.001
* Learning Rate Decay by factor of **0.1** if no improvement is seen
* Loss = Binary Crossentropy
* Initial Number of filters for Unet = 16
* Drop Out = 0.05
* Batch Size = 1

**Improvements Made on the Unet**
For improving the accuracy of the model, multiple techniques were applied and it was tried to get good results with good training and inference times. With the following changes the performance slightly increased and the training time significantly reduced.

**Removed a single Convolution Layer from the Conv2D block:** By doing so the network had simplified and it's speed increased.
**Added an Squeeze-and-Excitation block in front of the Convolution layer in Conv2d Block**: By doing this the performance of the network slight increased.

The accuracy of the Unet is slightly greater than DeepLabV3 and it is very light weight compared to DeepLab.



The following are the curves for accuracy, dice coefficient and f1-score for the Unet model:

