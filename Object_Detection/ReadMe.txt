TensorFlow Hub Object Detection with Faster R-CNN
================================================

Overview
--------
This project demonstrates how to build an object detection pipeline using TensorFlow 2, TensorFlow Hub, and a pre-trained Faster R-CNN model with an Inception-ResNet-v2 backbone. The model performs object detection on real-world images, generates bounding boxes around detected objects, and visualizes the results directly on the image.

The project explores the complete object detection workflow, including image preprocessing, model loading, inference, confidence thresholding, and visualization of predictions.

Key Features
------------
* Load pre-trained object detection models from TensorFlow Hub
* Perform inference on custom images
* Detect and classify multiple objects within a scene
* Generate bounding boxes around detected objects
* Display confidence scores and class labels
* Visualize detections using Matplotlib
* Experiment with urban street scenes and aerial imagery
* Analyze model limitations and domain shift

Model Information
-----------------
Detector:
* Faster R-CNN

Backbone:
* Inception-ResNet-v2

Pretraining Dataset:
* Open Images V4

TensorFlow Hub Model:
https://tfhub.dev/google/faster_rcnn/openimages_v4/inception_resnet_v2/1

Technologies Used
-----------------
* Python
* TensorFlow 2
* TensorFlow Hub
* NumPy
* Pillow (PIL)
* Matplotlib

Project Workflow
----------------
1. Load a pre-trained Faster R-CNN detector from TensorFlow Hub
2. Download and preprocess images
3. Convert images to TensorFlow tensors
4. Normalize image pixel values to the range [0,1]
5. Run object detection inference
6. Extract detection scores, classes, and bounding boxes
7. Overlay detections on the original image
8. Analyze results and model performance

Concepts Demonstrated
---------------------
* Object Detection
* Image Localization
* Transfer Learning
* Faster R-CNN Architecture
* Inception-ResNet-v2 Backbone
* TensorFlow Hub Model Reuse
* Bounding Box Regression
* Confidence Thresholding
* Computer Vision Inference Pipelines
* Domain Shift in Computer Vision

Results
-------
The model successfully detected a variety of objects including:

* People
* Bicycles
* Vehicles
* Buildings
* Windows
* Footwear
* Urban scene objects

The project also explored aerial imagery and demonstrated how object detection performance can degrade when the deployment data differs significantly from the model's training data.

Lessons Learned
---------------
* How modern object detection pipelines are constructed
* The role of feature extraction backbones in object detection
* Differences between image classification and object detection
* How confidence thresholds affect predictions
* The impact of domain shift on model performance
* Practical use of pre-trained models for rapid prototyping

Future Improvements
-------------------
* Compare Faster R-CNN with SSD MobileNet and YOLO
* Evaluate performance on drone and aerial imagery datasets
* Fine-tune the detector on a custom dataset
* Explore Non-Maximum Suppression (NMS) behavior
* Benchmark inference speed and memory usage
* Experiment with transformer-based detectors such as DETR and DINO

Repository Structure
--------------------
Object_Detection/
└── TFHub_Faster_RCNN_Object_Detection/
    ├── C3_W2_Lab_1_Simple_Object_Detection.ipynb
    ├── README.txt
    └── sample_outputs/

References
----------
TensorFlow Hub:
https://tfhub.dev/

Open Images Dataset:
https://storage.googleapis.com/openimages/web/index.html

Faster R-CNN:
Ren et al., "Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks" (2015)
