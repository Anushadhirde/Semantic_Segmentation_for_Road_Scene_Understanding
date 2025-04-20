## Semantic Segmentation for Road Scene Understanding using DeepLabV3+
# Project objective
The main goal of this project is to apply semantic segmentation to road scenes using the IDD dataset and DeepLabV3+. The work involves exploring the dataset’s structure, especially the 26 fine-grained level-3 classes specific to Indian roads. We used official AutoNUE tools to create accurate pixel-level masks for training. The DeepLabV3+ model was trained to handle complex scenes while preserving object boundaries. We evaluated its performance using the mIoU metric at 720p resolution, following AutoNUE standards. The results help assess how well the model works in unstructured traffic and show its potential for improving autonomous driving and intelligent transport systems.
# Dataset
The dataset used was the IDD-20K dataset, released as part of the AutoNUE Challenge 2021. It contains over 20,000 images of Indian road scenes, annotated at three levels of hierarchy. For this project, Level 3 annotations (26 classes) were used.

IDD-20K Part I

IDD-20K Part II

# Implementation
# Environment Setup

Developed on Windows 11 using Python 3.10.2


Created a virtual environment using venv


Installed libraries: numpy, pandas==1.2.1, tqdm, Pillow, scipy==1.1.0, imageio

# Dataset Preparation

Used the IDD-20K dataset from AutoNUE Challenge 2021 (Parts I and II)


Focused on Level 3 annotations with 26 semantic classes


Combined both dataset parts into one directory

# Label Generation

Annotations in JSON format converted to PNG masks using createLabels.py from AutoNUE’s GitHub


Each pixel in the PNG masks represents a class ID (0 to 25)


# Model: DeepLabV3+

Chosen for its strong performance in semantic segmentation tasks


Backbone: ResNet-101 pretrained on ImageNet


Encoder: Uses Atrous Spatial Pyramid Pooling (ASPP)


Decoder: Restores spatial detail for better accuracy


Implemented and trained using PyTorch

# Training

Split data into training and validation sets


Applied transformations: resizing, normalization, and tensor conversion


# Settings:

Optimizer: Adam


Learning rate: 0.001


Batch size: 8


Loss function: CrossEntropyLoss


Epochs: 50


# Prediction and Evaluation

Generated segmentation maps for validation images


Resized predicted and ground truth masks to 1280x720 using nearest neighbor interpolation


Evaluated performance using mean Intersection over Union (mIoU)


# Visualization

Overlaid predicted masks on original images using OpenCV


Helped visually assess model accuracy in complex scenes with poor lighting or heavy traffic

# Result

![Screenshot 2025-04-20 120244](https://github.com/user-attachments/assets/31807573-6ff3-4f9f-b9fb-bd15b4069bf9)
![Screenshot 2025-04-20 121104](https://github.com/user-attachments/assets/a590cbe9-55cd-4fbe-a70a-ce2d611074e6)
![Screenshot 2025-04-20 121235](https://github.com/user-attachments/assets/c08dea92-36ae-42f2-b298-19795b6402ba)
![Screenshot 2025-04-20 121439](https://github.com/user-attachments/assets/4599c479-5886-4cfa-b543-628aae2ce12f)


We used DeepLabV3+ to perform semantic segmentation on road scenes, successfully labeling each pixel into key categories like roads, vehicles, and pedestrians. The model produced accurate results, and the full pipeline from data prep to prediction worked well. This project shows how semantic segmentation can support safer, smarter AI-driven transportation.











