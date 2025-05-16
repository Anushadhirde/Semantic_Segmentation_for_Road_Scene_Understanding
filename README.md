# Semantic Segmentation for Road Scene Understanding using DeepLabV3+
# Project objective
To develop a semantic segmentation model for road scene understanding using DeepLabV3+.
The aim is to classify each pixel of street-level images into predefined classes like road, vehicle, pedestrian, etc.
This helps in creating detailed scene maps that support autonomous driving and traffic analysis.
We used the IDD dataset and trained the model using PyTorch for pixel-wise classification.

# Dataset
Name: Indian Driving Dataset - Segmentation Part 2

Type: Road scene dataset for semantic segmentation

Size: 8.5 GB 

Structure:

Images are divided into train, val, and test folders.

Corresponding semantic segmentation masks are provided for train and val.
Source: https://www.kaggle.com/datasets/sovitrath/indian-driving-dataset-segmentation-part-2

# Implementation
## Environment Setup 

We  started  the  implementation  on  Google  Colab  since  it's  a  great  cloud-based 
setup  for  testing  deep  learning  models.  We  turned  on  GPU  acceleration  to 
make  the  training  process  faster.  To  keep  everything  organized  and  make  sure 
we  didn’t  lose  progress  between  sessions,  we  also  connected  Google  Drive. 
That’s  where  we  stored  the  dataset  and  saved  model  checkpoints  so  we  could 
pick up right where we left off if needed. 

## Dataset Preparation

We  used  the  IDD  Segmentation  Part  2  dataset  from  Kaggle,  which  has  urban 
road  images  and  their  matching  grayscale  segmentation  masks.  Each  pixel  in 
the  mask  represents  a  specific  object  like  a  road,  car,  or  person.  We  organized 
everything  into  folders  and  used  a  custom  data  loader  to  make  sure  each 
image matched with the right mask. 

●  Download  IDD Part 2  from  Kaggle.

●  Organize the dataset into folders: images/ and masks/. 

●  Ensure that each image has a corresponding segmentation mask. 

## Data Preprocessing and Augmentation

All  images  and  masks  were  resized  to  256×256  for  consistency.  We 
normalized  the  images  using  ImageNet  stats  to  help  the  model  learn  better. 
The  mask  values  were  kept  unchanged  to  preserve  labels,  and  we  used  data 
augmentation to mimic different lighting and scene conditions. 

●  Resize all input images and masks to  256x256  resolution. 

●  Normalize pixel values (e.g., scale to 0–1 or mean-std normalization). 

●  Convert masks to  class labels  (0–25), ensuring correct mapping.


## Model: DeepLabV3+

For  the  semantic  segmentation  task,  the  DeepLabV3+  architecture  was 
chosen  due  to  its  strong  performance  in  preserving  object  boundaries  and 
capturing  context  at  multiple  scales.  The  model  utilized  a  ResNet50 
backbone  pre-trained  on  ImageNet.  To  suit  the  IDD  dataset,  which  includes 
26  semantic  classes  ,  the  final  classifier  layer  of  the  model  was  modified  to 
produce 26 output channels. 


## Training

Split data into training and validation sets


Applied transformations: resizing, normalization, and tensor conversion


## Settings:

●  Loss Function: CrossEntropyLoss with ignore_index=255 

●  Optimizer: Adam, learning rate = 0.0001 

●  Platform: Trained on Google Colab GPU 

●  Batching: Used DataLoader for efficient loading and preprocessing 

●  Epochs: Ran for 2 epochs 

●  Logging: Recorded training loss per epoch 


## Prediction and Evaluation

The  evaluation  was  conducted  on  the  validation  set  with  all  predictions  and 
ground  truths  resized  to  1280×720  resolution  ,  in  line  with  the  AutoNUE 
benchmark format. 

●  Pixel Accuracy 

●  Mean IoU 
These  metrics  indicate  that  the  model  was  able  to  reliably  distinguish 
between  various  elements  of  the  road  scene,  such  as  vehicles,  roads, 
pedestrians, and buildings, even in unstructured and cluttered environments.


## Visualization

Overlaid predicted masks on original images using OpenCV


Helped visually assess model accuracy in complex scenes with poor lighting or heavy traffic

# Result

![Screenshot 2025-05-16 113202](https://github.com/user-attachments/assets/75724c8e-bd3d-4969-9967-eebd4ecaa6e5)
![Screenshot 2025-05-16 113339](https://github.com/user-attachments/assets/38711819-6bf2-426a-8351-2746af70ff3f)
![Screenshot 2025-05-16 113546](https://github.com/user-attachments/assets/1eff0f1b-463c-4805-8b4b-4a4b1476fd35)
![Screenshot 2025-05-16 113748](https://github.com/user-attachments/assets/78ad9b9c-4cd7-49ee-a852-cec6572b7b16)


We used DeepLabV3+ to perform semantic segmentation on road scenes, successfully labeling each pixel into key categories like roads, vehicles, and pedestrians. The model produced accurate results, and the full pipeline from data prep to prediction worked well. This project shows how semantic segmentation can support safer, smarter AI-driven transportation.











