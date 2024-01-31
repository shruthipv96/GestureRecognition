# Gesture Recognition
---
## Case study assignment by IIIT Bangalore and Upgrad
---
> - Solving this assignment will give an idea of analysing the dataset and build a gesture recognition model to classify the video into one of the five gesture categories.
> - Developed as part of the Deep Learning Module required for Executive Post Graduate Program in Machine Learning and AI - IIIT,Bangalore.
---

## Table of Contents
* [General Information](#general-information)
* [Methodology](#methodology)
* [Repository contents](#repository-contents)
* [Conclusion](#conclusion)

## General Information
Imagine you are working as a data scientist at a home electronics company which manufactures state of the art smart televisions. You want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote.

The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:
 
| Gesture | Corresponding Action |
| --- | --- | 
| Thumbs Up | Increase the volume. |
| Thumbs Down | Decrease the volume. |
| Left Swipe | 'Jump' backwards 10 seconds. |
| Right Swipe | 'Jump' forward 10 seconds. |
| Stop | Pause the movie. |

Each video is a sequence of 30 frames (or images).

**Objective:**
1. **Generator**:  The generator should be able to take a batch of videos as input without any error. Steps like cropping, resizing and normalization should be performed successfully.

2. **Model**: Develop a model that is able to train without any errors which will be judged on the total number of parameters (as the inference(prediction) time should be less) and the accuracy achieved. As suggested by Snehansu, start training on a small amount of data and then proceed further.

3. **Write up**: This should contain the detailed procedure followed in choosing the final model. The write up should start with the reason for choosing the base model, then highlight the reasons and metrics taken into consideration to modify and experiment to arrive at the final model.

**Dataset:**
- The dataset is available in the Project_data.zip file
- The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use.
- The zip file contains a 'train' and a 'val' folder with two CSV files for the two folders. These folders are in turn divided into subfolders where each subfolder represents a video of a particular gesture. Each subfolder, i.e. a video, contains 30 frames (or images). Note that all images in a particular video subfolder have the same dimensions but different videos may have different dimensions. Specifically, videos have two types of dimensions - either 360x360 or 120x160 (depending on the webcam used to record the videos).
- Each row of the CSV file represents one video and contains three main pieces of information - the name of the subfolder containing the 30 images of the video, the name of the gesture and the numeric label (between 0-4) of the video.
  
## Methodology
- Generator
- Model
  - Convolutional 3D
  - Convolutional 2D + RNN
  - Transfer learning + RNN
  - Additional experiments

## Repository contents
| File | Description |
|:-----|:------------|
| Python notebook | It contains the complete detailed code along with necessary output to solve the problem. |
| README.md | This file briefs about the project. |
| Project_data.zip | This file contains the dataset and the explanation of the dataset is briefed above |
| Write-up pdf | This file contains a brief about the various experiments conducted. |
| model-00015-0.00159-1.00000-0.34987-0.88000.h5 | The best model obtained from the experiments. |
| AdditionalModels| This folder contains fewer more good models obtained during the experiments. |

## Conclusion
From the **38** different models built on different architectures, below are the good models from each variant,

| Model | Architecture | Total Parameters | Weight file size | Training Accuracy | Validation Accuracy | Training Loss | Validation Loss |
|:--|:--|:--|:--|:--|:--|:--|:--|
| model_8 | Conv3D | 87,429 | 1090 KB | 0.73152 | 0.63 | 0.64653 | 0.93146 |
| model_15| Conv2D + RNN | 225,477 | 2700 KB | 0.84804 | 0.82 | 0.34843 | 0.48902 |
| model_23| Conv2D + RNN | 13,781 | 254 KB | 0.75603 | 0.75 | 0.62860 | 0.67698 |
| **model_28** | **Transfer learning + RNN** | **3,511,365** | **23.3 MB** | **1.0** | **0.88** | **0.00159** | **0.34987** |

> - *We can ignore model_8 as we have better models from other variants*

> - Each model is good in different use cases, as few shown below,

| Memory Availability  | Performance Needed | Suggested model |
|:--|:--|:--|
| Abundant | High        | model_28 |
| Abundant | Moderate    | model_28 or model_15 |
| Moderate | Moderate    | model_15 |
| Less     | Moderate    | model_23 |

> - For this problem statement, we can consider **model_28** with the above shown metrics as the **best** model.

## Contact
Created by [Shruthip Venkatesh](https://github.com/shruthipv96) - feel free to contact me!