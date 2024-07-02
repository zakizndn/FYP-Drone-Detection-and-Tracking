# Drone Detection and Tracking in Distorted Surveillance Video

APM6168 - Final Year Project

Abstract - 

The widespread integration of drones across various industries has led to a surge in production efficiency and innovation. However, this increase in drone usage also brings forth significant threats to security and privacy concerns. In response, this project aimed to develop a robust drone detection system capable of effectively handling distorted surveillance video using YOLOv8 and implementing an efficient tracking system for predicting future drone positions in surveillance footage using LSTM/Bi-LSTM. This project utilised surveillance videos from the Drone Detection dataset, previously employed in the ICIP 2023 Challenge, comprising 650 videos featuring drones, birds, airplanes, and helicopters in both infrared (IR) and visible footage. Leveraging this dataset enabled a comprehensive evaluation of the detection and tracking system across various scenarios. Two datasets, visible and IR, were generated for object detection, employing YOLOv8 in different variants tailored to performance needs. For object tracking, centre coordinates were extracted from selected videos to create CSV files for training and testing. LSTM and Bi-LSTM layers with diverse configurations were utilised for tracking.

For object detection, analysis of the visible dataset demonstrated that YOLOv8s consistently outperformed other variants, achieving an impressive mAP of 92.3% and IoU of 90.9%. Conversely, on the IR dataset, all YOLOv8 models performed well, with YOLOv8l exhibiting the highest mAP of 97.9% and IoU of 94.9%, showcasing its proficiency in accurately detecting drones within distorted surveillance videos. Comparison with the ICIP 2023 Challenge's winner on the IR dataset highlighted the superiority of the proposed YOLOv8n model, which achieved higher evaluation metrics. For object tracking, the Bi-LSTM (32), Dropout (0.5) configuration was found to be the best, with the lowest MSE, RMSE, and MAPE of 0.00121, 0.03469, and 4.999%, respectively. This model demonstrated superior performance in accurately predicting the coordinates of moving objects and validated the effectiveness of the chosen configuration. In conclusion, this project has developed a robust drone detection and tracking system to address the rising issue of malicious drone activities that violate security and privacy. The system is designed not only to detect drones among other aerial entities but also to track their movements to assess potential threats.

#### Summary 


## Object Detection

## Object Tracking

