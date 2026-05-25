Transfer Learning with ResNet50 on CIFAR-10
===========================================

This project demonstrates transfer learning using a pretrained ResNet50 convolutional neural network on the CIFAR-10 image classification dataset.

The goal of the project is to explore how pretrained deep learning models can be adapted to new computer vision tasks using TensorFlow and Keras.

Project Overview
----------------
- Loaded and explored the CIFAR-10 dataset
- Preprocessed images using ResNet50 preprocessing utilities
- Upscaled CIFAR-10 images from 32x32 to 224x224 to match ResNet50 input requirements
- Used pretrained ImageNet weights from ResNet50
- Built a custom classification head for CIFAR-10 classes
- Trained and evaluated the network using transfer learning
- Visualized predictions, training accuracy, and validation accuracy
- Investigated image upscaling effects before feature extraction

Technologies Used
-----------------
- Python
- TensorFlow / Keras
- ResNet50
- NumPy
- Matplotlib

Dataset
-------
CIFAR-10 dataset:
https://www.cs.toronto.edu/~kriz/cifar.html

Model Architecture
------------------
- Pretrained ResNet50 backbone (ImageNet weights)
- Upsampling layer for resizing input images
- GlobalAveragePooling2D
- Fully connected dense layers
- Softmax output layer for 10-class classification

Key Concepts Demonstrated
-------------------------
- Transfer Learning
- Fine-Tuning
- Convolutional Neural Networks (CNNs)
- Image Preprocessing
- Feature Extraction
- Image Classification
- TensorFlow Model Building

Results
-------
The model achieved strong validation accuracy by leveraging pretrained ImageNet features and adapting them to CIFAR-10 classification.

One important observation from this project is that image upscaling does not improve image quality or add new visual information. Upscaling is used solely to adapt CIFAR-10 images to the input size expected by ResNet50.

Future Improvements
-------------------
- Freeze pretrained convolutional layers for feature extraction experiments
- Compare SGD vs Adam optimizers
- Add data augmentation
- Experiment with modern architectures such as EfficientNet or Vision Transformers
- Fine-tune deeper layers of ResNet50
- Evaluate confusion matrix and per-class accuracy

Author
------
Andrii Petrov

GitHub Portfolio Project focused on Computer Vision and Deep Learning.
