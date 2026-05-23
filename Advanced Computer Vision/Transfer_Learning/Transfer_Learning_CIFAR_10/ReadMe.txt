*** Cats vs Dogs Transfer Learning with InceptionV3 ***

This project demonstrates transfer learning for image classification using TensorFlow and the pretrained InceptionV3 model. 
The goal is to classify images of cats and dogs using a convolutional neural network trained on top of pretrained ImageNet features.

*** Project Overview ***

The notebook covers the complete deep learning workflow for computer vision:
   	* Downloading and preparing the Cats vs Dogs dataset
		* Splitting data into training and validation sets
		* Performing data augmentation
		* Using transfer learning with InceptionV3
		* Freezing pretrained convolutional layers
		* Adding custom classification layers
		* Training and validating the model
		* Visualizing training and validation accuracy
		* Running inference on custom images

*** Technologies Used: ***
		* Python
		* TensorFlow / Keras
		* InceptionV3
		* NumPy
		* Matplotlib

Instead of training a CNN from scratch, this project uses pretrained ImageNet weights from InceptionV3. 
This significantly reduces training time and improves performance on smaller datasets.

*** Data Augmentation ***

Image augmentation techniques such as:

		* rotation
		* shifting
		* zooming
		* shearing
		* horizontal flipping

are applied to improve model generalization and reduce overfitting.

*** Binary Classification ***

The model predicts whether an image belongs to one of two classes:

Cat
Dog


*** Model Architecture ***

The project uses:

		* pretrained InceptionV3 backbone (include_top=False)
		* frozen convolutional layers
		* custom dense layers for downstream classification

**** Final classification uses: ***

		* sigmoid activation
		* binary crossentropy loss
