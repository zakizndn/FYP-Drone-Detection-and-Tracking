
# Drone Detection and Tracking in Distorted Surveillance Video

APM6168 - Final Year Project 
 
The widespread integration of drones across various industries has led to a surge in production efficiency and innovation. However, this increase in drone usage also brings forth significant threats to security and privacy concerns. In response, this project aimed to develop a robust drone detection system capable of effectively handling distorted surveillance video using YOLOv8 and implementing an efficient tracking system for predicting future drone positions in surveillance footage using LSTM/Bi-LSTM. This project utilised surveillance videos from the Drone Detection dataset, previously employed in the ICIP 2023 Challenge, comprising 650 videos featuring drones, birds, airplanes, and helicopters in both infrared (IR) and visible footage. Leveraging this dataset enabled a comprehensive evaluation of the detection and tracking system across various scenarios. Two datasets, visible and IR, were generated for object detection, employing YOLOv8 in different variants tailored to performance needs. For object tracking, centre coordinates were extracted from selected videos to create CSV files for training and testing. LSTM and Bi-LSTM layers with diverse configurations were utilised for tracking.

For object detection, analysis of the visible dataset demonstrated that YOLOv8s consistently outperformed other variants, achieving an impressive mAP of 92.3% and IoU of 90.9%. Conversely, on the IR dataset, all YOLOv8 models performed well, with YOLOv8l exhibiting the highest mAP of 97.9% and IoU of 94.9%, showcasing its proficiency in accurately detecting drones within distorted surveillance videos. Comparison with the ICIP 2023 Challenge's winner on the IR dataset highlighted the superiority of the proposed YOLOv8n model, which achieved higher evaluation metrics. For object tracking, the Bi-LSTM (32), Dropout (0.5) configuration was found to be the best, with the lowest MSE, RMSE, and MAPE of 0.00121, 0.03469, and 4.999%, respectively. This model demonstrated superior performance in accurately predicting the coordinates of moving objects and validated the effectiveness of the chosen configuration. In conclusion, this project has developed a robust drone detection and tracking system to address the rising issue of malicious drone activities that violate security and privacy. The system is designed not only to detect drones among other aerial entities but also to track their movements to assess potential threats.

#### [Presentation Slide](https://www.canva.com/design/DAGHnztRQ3Y/ULN1ImqI7U4MAwR8lXzcXw/edit?utm_content=DAGHnztRQ3Y&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

## Object Detection 

### Quantitative Results 

#### Visible Dataset - Performance comparison of YOLOv8 models

Model | Precision | Recall | F1-score | Accuracy | mAP | IoU 
--- | --- | --- | --- |--- |--- |--- 
YOLOv8n | 0.904 | 0.849 | 0.876 | 0.923 | 0.890 | 0.906 
YOLOv8s | **0.919** | **0.894** | **0.906** | **0.928** | **0.923** | **0.909**
YOLOv8m | 0.911 | 0.851 | 0.880 | 0.921 | 0.902 | 0.908 
YOLOv8l | 0.899 | 0.861 | 0.880 | 0.926 | 0.899 | **0.909**

#### IR Dataset - Performance comparison of YOLOv8 models

Model | Precision | Recall | F1-score | Accuracy | mAP | IoU 
--- | --- | --- | --- |--- |--- |--- 
YOLOv8n | 0.973 | **0.971** | **0.972** | **0.943** | 0.978 | 0.946
YOLOv8s | **0.974** | 0.967 | 0.970 | **0.943** | 0.976 | 0.940
YOLOv8m | 0.969 | 0.965 | 0.967 | 0.942 | 0.977 | 0.942
YOLOv8l | 0.965 | 0.955 | 0.960 | 0.938 | **0.979** | **0.949**

#### Visible Dataset - Evaluation of YOLOv8 models during inference

Model | Number of layers | Number of parameters (M) | Complexity (GFLOPs) | Inference time (ms) | Training time (hours)
--- | --- | --- | --- |--- |---
YOLOv8n | 168 | 3.0 | 8.1 | 7.4 | 1.169 
YOLOv8s | 168 | 11.1 | 28.4 | 8.6 | 1.848
YOLOv8m | 218 | 25.8 | 78.7 | 18.0 | 3.533 
YOLOv8l | 268 | 43.6 | 164.8 | 33.8 | 5.411 

#### IR Dataset - Evaluation of YOLOv8 models during inference

Model | Number of layers | Number of parameters (M) | Complexity (GFLOPs) | Inference time (ms) | Training time (hours)
--- | --- | --- | --- |--- |---
YOLOv8n | 168 | 3.0 | 8.1 | 7.3 | 1.476
YOLOv8s | 168 | 11.1 | 28.4 | 8.7 | 2.312
YOLOv8m | 218 | 25.8 | 78.7 | 18.2 | 4.741 
YOLOv8l | 268 | 43.6 | 164.8 | 33.2 | 7.036 

### Qualitative Results

https://github.com/zakizndn/FYP-Drone-Detection-and-Tracking/assets/117178074/37f9b115-0ae5-4840-954e-c80277838ca8

https://github.com/zakizndn/FYP-Drone-Detection-and-Tracking/assets/117178074/561d4a88-4ffe-48f9-9c89-7db06b96e0a4

https://github.com/zakizndn/FYP-Drone-Detection-and-Tracking/assets/117178074/184b647a-70ba-4aeb-9d14-6306e04cba7c

https://github.com/zakizndn/FYP-Drone-Detection-and-Tracking/assets/117178074/0870cfd1-8a88-47dd-9492-81e8f9789be6


## Object Tracking

### Quantitative Results 

#### Performance comparison of different model configurations for Object Tracking with window size, n = 3

No | Model configuration | MSE | RMSE | MAPE (%) | Training time (hours)
--- | --- | --- | --- |--- |---
1 | LSTM (16), Dropout (0.5) | 0.00232 | 0.04815 | 8.947 | 0.747 
2 | LSTM (32), Dropout (0.5) | 0.00221 | 0.04694 | 7.377 | 0.752
3 | Bi-LSTM (16), Dropout (0.5) | 0.00124 | 0.03511 | 5.707 | 0.945
4 | Bi-LSTM (32), Dropout (0.5) | **0.00121** | **0.03469** | **4.999** | 0.972
5 | Bi-LSTM (32), Dropout (0.3) | 0.00168 | 0.03991 | 6.357 | 1.037
6 | Bi-LSTM (16), Dropout (0.5), Bi-LSTM (16), Dropout (0.5) | 0.00136 | 0.03675 | 6.461 | 1.309
7 | Bi-LSTM (32), Dropout (0.5), Bi-LSTM (32), Dropout (0.5) | 0.00133 | 0.03645 | 7.374 | 1.533

#### Performance comparison for Object Tracking model with different window sizes, n

n | MSE | RMSE | MAPE (%) | Training time (hours)
--- | --- | --- | --- |--- 
3 | **0.00121** | **0.03469** | **4.999** | 0.972 
6 | 0.00207 | 0.04451 | 7.959 | 0.850
9 | 0.00228 | 0.04700 | 7.797 | 1.280
12 | 0.00306 | 0.05324 | 7.986 | 1.170
15 | 0.00280 | 0.05122 | 7.434 | 1.460

### Qualitative Results 

https://github.com/zakizndn/FYP-Drone-Detection-and-Tracking/assets/117178074/6f0a0401-f38e-4ebe-a376-1c91422b927f

