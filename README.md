# food-101-classification
## About
Food-101 is a food image dataset containing 101,000 images, divided evenly across 101 different food categories. Each class contains 1,000 images. In this project, the provided dataset will be used to build a food classification model using Keras/TensorFlow. The goal is to train a model that can accurately identify and classify food images.

**Note:**
- Use tensorflow-gpu for faster training time
- You need to have the food-101 dataset in your working directory (otherwise you should change the paths to the food-101 file)
## Exploratory Data Analysis
<img width="1900" height="1200" alt="image" src="https://github.com/user-attachments/assets/a934c90a-8271-4009-a0ec-abcdf8bfe764" />
As shown in the sample images, the image quality varies across the dataset. The images have different backgrounds, lighting conditions, and angles. Some images may also be misleading. For example, an image labeled as lobster soup may mostly show broth without any visible lobster. All of these factors can make it harder for the model to learn the features of each food category and may affect its classification performance.
