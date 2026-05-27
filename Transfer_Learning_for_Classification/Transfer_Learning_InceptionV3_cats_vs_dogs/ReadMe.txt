# Cats vs Dogs Image Classification using Transfer Learning (InceptionV3)

## Project Overview

This project demonstrates transfer learning for computer vision using TensorFlow and the pretrained InceptionV3 convolutional neural network. The model is trained to classify images of cats and dogs using a relatively small custom dataset while leveraging features learned from the ImageNet dataset.

The project was implemented in Google Colab as part of my deep learning and computer vision learning path.

---

## Objectives

- Learn the fundamentals of transfer learning
- Understand convolutional neural networks (CNNs)
- Apply data augmentation techniques
- Train a binary image classifier
- Visualize model performance
- Perform inference on custom images

---

## Technologies Used

- Python
- TensorFlow / Keras
- InceptionV3
- NumPy
- Matplotlib
- Google Colab

---

## Dataset

Dataset:
Microsoft Cats and Dogs dataset (derived from Kaggle Dogs vs Cats)

The dataset contains:
- 12,500 cat images
- 12,500 dog images

The project automatically:
- downloads the dataset
- extracts the files
- removes corrupt images
- splits the data into training and validation sets

---

## Project Workflow

### 1. Data Preparation
- Download and extract dataset
- Create training/testing directory structure
- Split dataset into:
  - 90% training
  - 10% validation/testing

### 2. Data Augmentation
Image augmentation was applied using ImageDataGenerator to improve generalization and reduce overfitting.

Augmentation techniques:
- rotation
- width shifting
- height shifting
- zooming
- shearing
- horizontal flipping

### 3. Transfer Learning
The project uses a pretrained InceptionV3 backbone trained on ImageNet.

Key steps:
- load pretrained weights
- remove the original classification head (`include_top=False`)
- freeze convolutional layers
- add custom dense layers for binary classification

### 4. Model Architecture

Base model:
- InceptionV3 pretrained on ImageNet

Custom classification head:
- Flatten layer
- Dense(1024, activation='relu')
- Dense(1, activation='sigmoid')

Loss Function:
- binary_crossentropy

Optimizer:
- RMSprop

---

## Training Results

Training was performed for 20 epochs.

Final performance:
- Training Accuracy: ~96.5%
- Validation Accuracy: ~98.4%
- Validation Loss: ~0.044

The model demonstrated strong generalization performance with minimal overfitting.

---

## Key Learning Outcomes

This project helped reinforce understanding of:
- transfer learning workflows
- pretrained CNN architectures
- binary image classification
- TensorFlow/Keras pipelines
- data augmentation
- training vs validation metrics
- overfitting and generalization
- inference pipelines for custom images

---

## Example Inference

The trained model can classify uploaded images as:
- cat
- dog

using sigmoid probability output.

---

## Potential Future Improvements

Possible next steps:
- fine-tuning deeper InceptionV3 layers
- experimenting with EfficientNet or Vision Transformers
- implementing Grad-CAM visualizations
- exporting model to TensorFlow Lite
- deploying as a web application
- adding confusion matrix and precision/recall metrics

---

## Repository Structure

.
├── notebook.ipynb
├── README.txt
└── sample_predictions/

---

## References

- TensorFlow/Keras Documentation
- DeepLearning.AI TensorFlow Developer Specialization
- InceptionV3 Paper:
  "Rethinking the Inception Architecture for Computer Vision" (2015)

---

## Author

Andrii Petrov

Computer Vision | Deep Learning | Medical Imaging | Applied Machine Learning
