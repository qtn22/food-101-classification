# food-101-classification
## About
Food-101 is a food image dataset containing 101,000 images, divided evenly across 101 different food categories. Each class contains 1,000 images. In this project, the provided dataset will be used to build a food classification model using Keras/TensorFlow. The goal is to train a model that can accurately identify and classify food images.

**Note:**
- Use tensorflow-gpu for faster training time
- You need to have the food-101 dataset in your working directory (otherwise you should change the paths to the food-101 file)
## Exploratory Data Analysis
<img width="1900" height="1200" alt="image" src="https://github.com/user-attachments/assets/a934c90a-8271-4009-a0ec-abcdf8bfe764" />
As shown in the sample images, the image quality varies across the dataset. The images have different backgrounds, lighting conditions, and angles. Some images may also be misleading. For example, an image labeled as lobster soup may mostly show broth without any visible lobster. All of these factors can make it harder for the model to learn the features of each food category and may affect its classification performance.

## Data Augmentation
To train a good neural network, an image data generator from Keras is used for image tranformation to expand the dataset and to reduce the overfitting problem.
<img width="914" height="657" alt="image" src="https://github.com/user-attachments/assets/40810a74-808a-4bfa-a432-17056381ba0a" />
The images are slightly flipped and zoomed in as part of the data augmentation process. These changes can help the model learn important features more effectively by exposing it to different variations of the same image. This may improve the model’s ability to generalize and produce better classification results.
## Model
**Transfer Learning:** The ConvNeXtTiny base model is frozen so that its pre-trained ImageNet weights remain unchanged during training. Instead of training the entire model from scratch, the pre-trained layers are used as a feature extractor to capture general image patterns such as shapes, textures, and edges. This reduces training time and allows the model to benefit from knowledge learned from a large-scale image dataset. Then, new custom layers are added on top to learn features specific to the Food-101 classification task.

**Dropout:** Dropout layers with a rate of 0.3 are added after each dense layer. Dropout helps reduce overfitting by randomly disabling some neurons during training, forcing the model to learn more general features instead of memorizing the training images.

**Optimizer:** The model uses the Adam optimizer, which is commonly used because it adapts the learning rate during training and often converges faster than traditional gradient descent methods.

**Activation Function:** ReLU activation is used in the dense layers to help the model learn non-linear patterns efficiently and reduce the chance of vanishing gradients. The final output layer uses softmax activation because this is a multi-class classification problem with 101 food categories. Softmax converts the output values into probabilities for each class.

**Early Stopping:** Early stopping is used to monitor val_loss. If the validation loss does not improve for 3 epochs, training stops automatically. There is the option helps restore the model weights from the epoch with the best validation loss. This helps prevent overfitting and keeps the best-performing version of the model.
