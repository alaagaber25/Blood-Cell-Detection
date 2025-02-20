# Blood Cell Detection using YOLOv12

## Overview
This project implements a blood cell detection system using the YOLOv12 object detection model. Our primary goal is to accurately detect and classify red blood cells (RBC) and white blood cells (WBC) in microscopy images.

## Project Workflow
1. **Data Analysis**  
   We started by analyzing our dataset, which included microscopy images along with a CSV file containing the bounding box coordinates (`xmin`, `ymin`, `xmax`, `ymax`) and labels for each cell. During this analysis, we discovered that the dataset was highly imbalanced with significantly more RBC instances (2237) compared to WBC (103).

2. **Handling Imbalanced Data**  
   To address the class imbalance:
   - We **extracted the minority class (WBC)** into separate images.
   - We applied various **data augmentation techniques** to the WBC images to increase their count and diversity. The augmentations include:
     - Horizontal flip
     - Vertical flip
     - Combined horizontal and vertical flip

3. **Bounding Box Extraction**  
   The annotations for each image were read from a CSV file. This file provided us with the precise coordinates for each bounding box, ensuring that the model learns the correct regions of interest for both RBC and WBC.

4. **Model Training**  
   With a balanced dataset—thanks to our augmentation steps—we trained the YOLOv12 model. The training process leverages the preprocessed images along with their bounding box annotations to improve the detection accuracy, particularly for the previously underrepresented WBC class.

5. **Evaluation and Visualization**  
   After training, we evaluated the model's performance by visualizing the label distribution and assessing metrics such as precision, recall, and mean Average Precision (mAP). These evaluations helped us confirm that our data augmentation and extraction methods significantly improved the detection capabilities of the model.

## Dataset
- **Images**: Microscopy images of blood cells.
- **Annotations**: Bounding box coordinates and labels (RBC, WBC) stored in a CSV file.
- **Challenge**: Imbalance in the number of RBC vs. WBC images.
- **Solution**: Extracted and augmented the minority class (WBC) using various flip techniques.

## Results
The implemented pipeline significantly improves the YOLOv12 model's performance, especially for detecting the minority WBC class. By extracting the minority class images and applying horizontal, vertical, and combined flips, we achieved a more balanced dataset which in turn led to better model accuracy and robustness.
