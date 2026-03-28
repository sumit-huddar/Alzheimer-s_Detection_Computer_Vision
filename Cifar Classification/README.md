## Team Task

Task 1 and Task 2 (Dhyanav)

Task 1

The CIFAR10 dataset is already clean, shuffled and neatly labelled. So, I directly moved to data augmentation. I divided 60,000 images of CIFAR-10 into 6 batches of 10,000 each. They were used for flipping, rotating, cropping, adding noise, cut-out and mixup.

Cut-out: I randomly cut a square of 6 by 6 from the image. Using this technique helps the model learn better since it tries to identify an image without a certain part. It reduces dependence on specific parts of the image. I decided to use 6 by 6 after some experimentation. I feel it was in the middle, not too small to be practically ineffective and not too large to remove all key features entirely.

Mixup: It selects a random image and imposes it on chosen images. The formula used is  
	Xnew \= alpha\*X1 \+ (1-alpha)\*X2  
Here, Xnew is the final result, X1 is the base image and X2 is the image that is being imposed. After some experimentation, I used alpha \= 0.75.

Then, I combined it into the original dataset, doubling its size. Then, I split data. 95,000 images for training, 10,000 for validation and 15,000 for testing.

Now, I moved to task 2

Task 2

ANN:  
I started with 2 hidden layers, but gradually increased the layers so it was computationally viable. Finally, there are 4 layers. I also doubled the number of neurons in each layer and stuck with it since it increased accuracy without overfitting.

I trained for 15 epochs. Since, loss is steadily decreasing, implementing early stopping was not useful. Increasing epochs led to an increase in difference between training accuracy and test accuracy. I finally decided to use 15 epochs since the difference was only 5%.

![](image1.png)  
![](image2.png) 

CNN:  
I used a similar process as in ANN. Gradually increasing the number of layers and number of neurons in each layer till I was satisfied with the result. I tried implementing early stopping but it was useless as only the last three layers were showing signs of saturation and early stopping evaluates accuracy of three layers before stopping training.

In both, I used ADAM optimiser, so learning rate was not a part of experimentation as ADAM adjusts learning rate accordingly. I increased batch size from 32 to 256 to speed up training while also maintaining accuracy. (After 256, accuracy started to drop.)

![](image3.png)  
![](image4.png)   
I also trained the same models, ANN and CNN on raw CIFAR10 data and the difference in accuracy was significant.

![](image5.png) 
![](image6.png) 

On the CNN model, I implemented one-pixel attack. THis is a type of attack where the attacker randomly selects a pixel and manipulates it. It is known to reduce accuracy of the model by a significant margin. But since I implemented cutout in data augmentation, model accuracy only dropped from 91.24% to 83.34

![](image7.png) 

Task 3-6(Sumit and Shikhar)  
AlexNet, LeNet, VGG16(Sumit)

VGG16: \~138M parameters. A very deep model with 13 convolutional layers. 

Epochs: 5(same problem as AlexNet)

Batch Size: 128

![](image14.png) 
![](image15.png) 

![](image16.png) 
Observations

- The model achieves an overall accuracy of ~78% on the dataset.
- ROC-AUC score (~0.97) indicates strong class separability.
- Some classes(like class 3) show lower precision, suggesting confusion with similar classes.
- Performance varies across classes, indicating potential imbalance or feature overlap.
  
| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC(OvA) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| LeNet | 0.64 | 0.66 | 0.64 | 0.64 | 0.9401 |
| AlexNet | 0.75 | 0.77 | 0.75 | 0.75 | 0.9706 |
| VGG16 | 0.78 | 0.79 | 0.78 | 0.78 | 0.9746 |

 (here precision, recall, and f1 score are the macro avg)

AlexNet: \~60M parameters. A deeper architecture with 5 convolutional layers. It handles larger input variations better.

Epochs: Initially tried 15 but it was taking much longer than LeNet so switched to 5\.

Batch Size-128

![](image11.png) 

![](image12.png) 

![](image13.png) 

Observations

- The model achieves an overall accuracy of ~75%, slightly lower than VGG16.
- ROC-AUC score (~0.97) indicates strong class separability despite lower accuracy.

- Performance varies across classes:
  - High precision but lower recall for some classes (e.g., class 2) suggests the model is conservative and misses true instances.
  - Class 4 shows high recall (0.89) but low precision (0.52), indicating many false positives.

- Compared to deeper models, AlexNet struggles to generalize well across all classes, likely due to its relatively shallow architecture.

- Overall, the model performs reasonably well but shows inconsistencies across classes, suggesting room for improvement with deeper or more regularized architectures.

LeNet: \~60K parameters. A shallow network with 2 convolutional layers.  
Epochs-15  
Batch Size-128  
![](image8.png)  
![](image9.png) 

![](image10.png) 

Observations

- The model achieves an overall accuracy of ~64%, significantly lower than both AlexNet and VGG16.
- ROC-AUC score (~0.94) is also lower, indicating weaker class separation.

- Performance across classes is inconsistent:
  - Several classes (e.g., class 3 and 2) show low precision and recall, indicating difficulty in learning discriminative features.
  - The model struggles especially with more complex classes, likely due to limited representational capacity.

- Compared to AlexNet and VGG16, LeNet is much simpler and was originally designed for simpler datasets, which explains the performance gap.

- The results highlight the importance of deeper architectures for complex image classification tasks like CIFAR-10.



VGG16: \~138M parameters. A very deep model with 13 convolutional layers. 

Epochs: 5(same problem as AlexNet)

Batch Size: 128

![](image14.png) 
![](image15.png) 

![](image16.png) 
Observations

- The model achieves an overall accuracy of ~78% on the dataset.
- ROC-AUC score (~0.97) indicates strong class separability.
- Some classes(like class 3) show lower precision, suggesting confusion with similar classes.
- Performance varies across classes, indicating potential imbalance or feature overlap.
  
| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC(OvA) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| LeNet | 0.64 | 0.66 | 0.64 | 0.64 | 0.9401 |
| AlexNet | 0.75 | 0.77 | 0.75 | 0.75 | 0.9706 |
| VGG16 | 0.78 | 0.79 | 0.78 | 0.78 | 0.9746 |

 (here precision, recall, and f1 score are the macro avg)

| Factor | LeNet | AlexNet | VGG16 |
| :---: | :---: | :---: | :---: |
| Overfitting | High | Medium | Low |
| Training Time | Low | Medium | High |
| Generalization | Poor | Decent | Good |

Conclusion:

\-VGG16 gave the best results in terms of accuracy, F1-score, and AUC.

\-LeNet was unsuitable for CIFAR-10 due to its simplicity.

\-AlexNet was a good balance between complexity and performance.

# TRANSFER LEARNING IMPLEMENTATION

# VGG 19, ResNet50, ResNet152 (Shikhar)

VGG19 \-  
144M Parameters  
Has Three more convolution layers than VGG16.  
Epochs \- 5  
![](image17.png)  
![](image18.png) 
![](image19.png)![](image20.png)

## Resnet50 and 152

Resnets employ something called skip connections, which makes some neurons bypass some layers in the middle, minimising the exploding gradient problem and allowing deeper richer feature extraction.   
While they are generally better than VGG, for a problem simple like MNIST, it is **overkill** and leads to lesser accuracy than VGG and simpler models.  
![](image21.png)![](image22.png)

####  Also, another conclusion that we can take from this is, that training models from scratch would always lead to better results than transfer learning since we lose feature extraction in compensation of computation cost.

We could also train for more epochs to further illustrate benefits of transfer learning.  
