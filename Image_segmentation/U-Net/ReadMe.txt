# U-Net Image Segmentation on Oxford-IIIT Pet Dataset

## Overview

This project implements a U-Net convolutional neural network for semantic image segmentation using TensorFlow and Keras. The model is trained on the Oxford-IIIT Pet Dataset to classify each pixel in an image into one of three classes:

* Pet
* Background
* Outline

The project demonstrates the complete workflow for a semantic segmentation task, including data preprocessing, augmentation, model construction, training, evaluation, and visualization of segmentation masks.

---

## Dataset

**Oxford-IIIT Pet Dataset**

The dataset contains over 7,000 images of cats and dogs from 37 different breeds. Each image includes a corresponding segmentation mask with pixel-level annotations.

Classes used in this project:

| Label | Class      |
| ----- | ---------- |
| 0     | Pet        |
| 1     | Background |
| 2     | Outline    |

Images and masks are loaded directly from TensorFlow Datasets (TFDS).

---

## Data Preprocessing

The preprocessing pipeline includes:

* Image resizing to 128 × 128 pixels
* Pixel value normalization to [0,1]
* Segmentation mask label adjustment
* Random horizontal flipping for data augmentation
* Efficient TensorFlow Dataset pipelines with batching, caching, shuffling, and prefetching

---

## Model Architecture

The segmentation model is based on the U-Net architecture consisting of:

### Encoder (Downsampling Path)

* Repeated Conv2D + ReLU blocks
* MaxPooling layers for spatial reduction
* Dropout regularization

### Bottleneck

* High-capacity convolutional feature extraction layer

### Decoder (Upsampling Path)

* Conv2DTranspose layers for upsampling
* Skip connections from encoder feature maps
* Feature concatenation to preserve spatial information

### Output Layer

* 1×1 convolution with Softmax activation
* Produces pixel-wise class probabilities for three segmentation classes

---

## Training

* Framework: TensorFlow / Keras
* Optimizer: Adam
* Loss Function: Sparse Categorical Crossentropy
* Batch Size: 64
* Epochs: 10

---

## Evaluation

Model performance is evaluated using:

* Pixel Accuracy
* Intersection over Union (IoU)
* Dice Score

These metrics are computed both globally and on a per-class basis.

---

## Results

The trained model successfully generates segmentation masks that identify pets, background regions, and object boundaries. Skip connections in the U-Net architecture help preserve fine spatial details and improve segmentation quality compared to standard encoder-decoder networks.

---

## Technologies Used

* Python
* TensorFlow
* Keras
* TensorFlow Datasets (TFDS)
* NumPy
* Matplotlib

---

## Learning Outcomes

This project demonstrates practical experience with:

* Semantic image segmentation
* U-Net architecture
* TensorFlow data pipelines
* Data augmentation techniques
* Pixel-wise classification
* Evaluation using IoU and Dice metrics
