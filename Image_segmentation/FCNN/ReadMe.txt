FCN-8 Semantic Segmentation on CamVid Dataset
=============================================

Author: Andrii Petrov, PhD

Project Overview
----------------

This project implements a Fully Convolutional Network (FCN-8) for semantic image segmentation 
using TensorFlow and Keras. The model is trained on a subset of the CamVid dataset and performs pixel-wise classification of urban street scenes.

Unlike image classification, where a single label is assigned to an entire image, 
  semantic segmentation predicts a class label for every pixel in the image. The output 
is a segmentation mask where each pixel corresponds to a semantic category such as road, building, vehicle, or pedestrian.

This project was completed as part of the DeepLearning.AI Advanced Computer Vision 
specialization and serves as an introduction to modern segmentation architectures.

Dataset
-------

The project uses a processed subset of the CamVid (Cambridge-driving Labeled Video Database) dataset.

CamVid contains video frames captured from a vehicle driving through urban environments. Each frame has been manually annotated at the pixel level to create ground-truth segmentation masks.

Dataset structure:

dataset1/
│
├── images_prepped_train/
├── annotations_prepped_train/
├── images_prepped_test/
└── annotations_prepped_test/

Classes
-------

The segmentation masks contain 12 semantic classes:

0  - Sky
1  - Building
2  - Column/Pole
3  - Road
4  - Sidewalk
5  - Vegetation
6  - Traffic Light
7  - Fence
8  - Vehicle
9  - Pedestrian
10 - Bicyclist
11 - Void

Ground Truth Annotations
------------------------

Each annotation image is a label map where each pixel stores an integer representing the class ID.

Example:

Road pixel      -> 3
Vehicle pixel   -> 8
Sky pixel       -> 0

The masks were manually created by human annotators who labeled every pixel in the original image.

Model Architecture
------------------

Encoder:
- VGG16 pretrained on ImageNet
- Five convolutional blocks
- Max pooling after each block
- Additional Conv6 and Conv7 layers

Decoder:
- FCN-8 architecture
- Transposed convolutions (deconvolutions)
- Skip connections from Pool3 and Pool4
- Softmax output layer

Architecture Flow:

Input Image (224x224x3)
        |
      VGG16
        |
      Pool3 -----------+
        |              |
      Pool4 ------+    |
        |         |    |
      Pool5       |    |
        |         |    |
      Conv6       |    |
        |         |    |
      Conv7       |    |
        |         |    |
     Upsample <---+    |
        |              |
     Upsample <--------+
        |
     Upsample
        |
      Softmax
        |
 Segmentation Mask

Data Preprocessing
------------------

Input Images:
- Resize to 224x224
- Normalize pixel values to [-1, 1]

Annotations:
- Resize to 224x224
- Convert class-index masks into one-hot encoded masks

Original mask shape:

(224, 224, 1)

One-hot encoded shape:

(224, 224, 12)

Example:

Original label:

[0, 1, 2]

One-hot representation:

[1,0,0]
[0,1,0]
[0,0,1]

Training Configuration
----------------------

Framework:
- TensorFlow 2.x
- Keras API

Optimizer:
- SGD
- Learning rate = 0.01
- Momentum = 0.9
- Nesterov acceleration enabled

Loss Function:
- Categorical Crossentropy

Batch Size:
- 64

Epochs:
- 170

Input Resolution:
- 224 x 224

Transfer Learning
-----------------

The encoder uses pretrained VGG16 weights trained on ImageNet.

Using pretrained weights provides:

- Faster convergence
- Better feature extraction
- Improved segmentation performance
- Reduced training time

Visualization Utilities
-----------------------

The notebook includes utilities for:

- Viewing image/mask pairs
- Colorizing segmentation masks
- Displaying predictions
- Computing IoU metrics
- Computing Dice scores

The visualization pipeline converts integer label maps into RGB masks using a predefined color palette.

Evaluation Metrics
------------------

Pixel Accuracy
--------------
Measures the percentage of correctly classified pixels.

Intersection over Union (IoU)
-----------------------------

IoU = Intersection / Union

Measures overlap between predicted and ground-truth masks.

Dice Score
----------

Dice = 2 * Intersection / (Prediction + Ground Truth)

Frequently used in medical image segmentation.

Results
-------

Training accuracy increased from approximately 8% to over 80% during training.

Typical performance:

Training Accuracy:
~82-85%

Validation Accuracy:
~80-85%

The model successfully segments:

- Roads
- Buildings
- Sky
- Vegetation
- Vehicles

More challenging classes include:

- Pedestrians
- Traffic lights
- Bicyclists

These classes occupy fewer pixels and appear less frequently in the training set.

Key Concepts Learned
--------------------

1. Semantic Segmentation
   Pixel-level image classification.

2. Fully Convolutional Networks
   Converting classification networks into dense prediction networks.

3. Transfer Learning
   Leveraging pretrained ImageNet features.

4. Skip Connections
   Recovering spatial information lost through pooling.

5. Transposed Convolutions
   Learnable upsampling operations.

6. One-Hot Encoded Masks
   Representing segmentation labels for multi-class classification.

Limitations
-----------

This implementation is intended for educational purposes.

Limitations include:

- VGG16 is computationally expensive
- FCN-8 produces coarse object boundaries
- No attention mechanisms
- No batch normalization
- No transformer-based components
- Lower accuracy than modern segmentation architectures

Modern Alternatives
-------------------

State-of-the-art segmentation models include:

- U-Net
- DeepLabV3+
- PSPNet
- SegFormer
- Mask2Former
- Swin Transformer
- nnU-Net (medical imaging)

Potential Improvements
----------------------

Possible future enhancements:

- Replace VGG16 with ResNet50 or EfficientNet
- Add Batch Normalization
- Use DeepLabV3+ decoder
- Train on higher-resolution images
- Use Dice Loss or Focal Loss
- Perform data augmentation
- Evaluate using mean IoU (mIoU)
- Experiment with transformer-based segmentation architectures

Files
-----

Main notebook:

C3_W3_Lab_1_VGG16-FCN8-CamVid.ipynb

Primary components:

- Dataset loading
- Preprocessing pipeline
- VGG16 encoder
- FCN-8 decoder
- Training loop
- Visualization utilities
- Evaluation metrics

References
----------

Long, Shelhamer, Darrell
"Fully Convolutional Networks for Semantic Segmentation"
CVPR 2015

Simonyan and Zisserman
"Very Deep Convolutional Networks for Large-Scale Image Recognition"
2014

CamVid Dataset:
http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/

DeepLearning.AI
Advanced Computer Vision Specialization

Summary
-------

This project demonstrates the implementation of a classical semantic segmentation architecture using a pretrained VGG16 backbone and an FCN-8 decoder. Although FCN-8 has largely been replaced by more advanced architectures, it remains an important milestone in the evolution of dense prediction models and provides a strong foundation for understanding modern segmentation networks such as U-Net, DeepLab, SegFormer, and Mask2Former.
