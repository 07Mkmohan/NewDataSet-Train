
# Near Duplicate Image Search using Deep Learning (VGG19)

# Introduction
This project demonstrates a near duplicate image search system using the VGG19 model and the `DeepImageSearch` library. It allows you to index a dataset of images and retrieve visually similar images based on a query image.<br>

Installation: Make sure you have DeepImageSearch installed. <br>
If not, install it using pip:<br>
Mount Google Drive: Mount your Google Drive to access your dataset stored there:<br>
Directory Structure: Ensure your images are stored in a directory on your Google Drive. Update the drive_dir variable with the path to your image directory.<br>


Certainly! Based on the code snippet you provided, here's how you can structure the README section for your GitHub repository. This assumes you're using the `DeepImageSearch` library for near duplicate image search with VGG19 on Google Colab.

---

# Requirements
- Python 3.x
- DeepImageSearch
- Google Colab (for this example)
- TensorFlow (automatically installed with DeepImageSearch)
- Keras (automatically installed with DeepImageSearch)
- NumPy
- OpenCV (typically pre-installed in Colab)
- Matplotlib (for visualization)

# Setup Instructions

# 1. Clone and Install Dependencies

```bash
!pip install DeepImageSearch
from DeepImageSearch import Load_Data, Search_Setup
from google.colab import drive

# Mount Google Drive
drive.mount('/content/drive')
import os

# Path to the directory in your Google Drive
drive_dir = '/content/drive/MyDrive/dataset/dataset'

# List all files in the directory
file_list = os.listdir(drive_dir)
print(file_list)
```

# 2. Load Data

```python
# Load images from a folder
image_list = Load_Data().from_folder(['/content/drive/MyDrive/dataset/dataset'])
print("Total Image Count:", len(image_list))
print("Samples:")
print(image_list[:20])
```

# 3. Set up the Search Engine

```python
# Set up the search engine
st = Search_Setup(image_list=image_list, model_name='vgg19', pretrained=True, image_count=100)
```

# 4. Index Images

```python
# Index the images
st.run_index()
```

# 5. Add New Images to the Index (Optional)

```python
# Add new images to the index
st.add_images_to_index(image_list[50:100])
```

# 6. Get Similar Images

```python
# Get similar images
similar_images = st.get_similar_images(image_path=image_list[4], number_of_images=10)
print(similar_images)
```

# 7. Plot Similar Images (Optional)

```python
# Plot similar images
st.plot_similar_images(image_path=image_list[4], number_of_images=10)
```

# Example Usage

Include an example of how to run your application or scripts for searching near duplicate images here, detailing how to mount Google Drive, load data, set up the search engine, and perform searches.

```python
# Example usage
drive.mount('/content/drive')

# Load data
image_list = Load_Data().from_folder(['/content/drive/MyDrive/dataset/dataset'])

# Set up search engine
st = Search_Setup(image_list=image_list, model_name='vgg19', pretrained=True, image_count=100)

# Index images
st.run_index()

# Get similar images
similar_images = st.get_similar_images(image_path=image_list[4], number_of_images=10)
print(similar_images)

# Plot similar images
st.plot_similar_images(image_path=image_list[4], number_of_images=10)
```

# Contributing
Contributions to this project are welcome. Please fork the repository, make improvements, and submit a pull request.

 This structure should help users understand how to set up and utilize your near duplicate image search system effectively with VGG19 using the `DeepImageSearch` library on Google Colab.
