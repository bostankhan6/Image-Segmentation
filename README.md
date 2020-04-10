# Image-Segmentation-Unet-DeepLabV3-Segnet

Semantic Segmentation models have been trained on the MoNuSeg Dataset comprising of 30 H&E stained tissue trainins Images of 30 patients with tumors of different organs. The dataset also has a subset of 14 images for validation of the models. The images were taken at 40 times magnification. 

https://monuseg.grand-challenge.org/Data/

Three architectures have been used for learning purposes:

* Segnet
* Unet 
* DeepLabV3

The implementation and results of each have been provided in their respective Jupyter notebooks in this repository.

The metrics that have been used are Loss, Accuracy, Dice Coefficient and F1-Score:

|          | Modified Unet | DeepLabV3 | Segnet |
|----------|:-------------:|:---------:|:------:|
| Loss     |     0.3436    |   0.4292  | 0.6813 |
| Accuracy |     91.40%    |   90.59%  | 83.26% |
| Dice     |     0.7728    |   0.7589  | 0.3226 |
| F1       |     0.7889    |   0.7766  | 0.5792 |

 The The best results have been obtained with the **Modified Unet**

The performance plots for the models are:

### Unet Loss

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/Unet_loss.jpg "Unet Loss")

### Deel Lab V3 Loss:

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/deeplab_loss.jpg "Deep Lab V3+ Loss")

### Segnet Loss:

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/segnet_loss.png "Segnet Loss")

## Modified Unet

## Improvements Made on the Unet
For improving the accuracy of the model, multiple techniques were applied in order to get good results with good training and inference times. With the following changes the performance slightly increased and the training time significantly reduced (On Google Colab, 50 Epocs in just **6 minutes!**).

### Removed a single Convolution Layer from the Conv2D block: 
By doing so the network has simplified and it's speed has dramatically increased.

### Added a Squeeze-and-Excitation block in front of the Convolution layer in Conv2d Block: 
By doing this the performance of the network slightly increased.

### Removed the middle dense layer from SE Block that decreases (normally by a ratio of 16) the number of neurons that are input to the final dense layer of SE block for generating excitation values.

The settings for Unet that were used are given below:
* Optimizer = Adam
* Initial Learning Rate = 0.001
* Learning Rate Decay by factor of **0.1** if no improvement is seen
* Loss = Binary Crossentropy
* Initial Number of filters for Unet = 16
* Drop Out = 0.05
* Batch Size = 16

10% of the training set was used as validation set during training of the network.

Actual image size is 1000x1000 but for training purposes patching of 256x256 has been implemented.

The accuracy of the Unet is slightly greater than DeepLabV3 and it is very light weight compared to DeepLab.

Following are the curves for accuracy, dice coefficient and f1-score for the Unet model:

### Unet_Accuracy
![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/accuracy.jpg "Unet Accuracy")

### Unet Dice_Score
![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/dice.jpg "Unet Dice Score")

### F1_Score
![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/f1.jpg "Unet F1 Score")

## Test Set Results 

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/test1.jpg "Test1")

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/test2.jpg "Test2")

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/test3.jpg "Test3")

![alt text](https://github.com/bostankhan6/Image-Segmentation-Unet-DeepLabV3-Segnet/blob/master/plots_and_images/test4.jpg "Test4")
