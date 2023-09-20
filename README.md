# AVM-SLAM: Semantic Visual SLAM with Multi-Sensor Fusion in a Bird’s Eye View for Automated Valet Parking

**Authors:** Ye Li<sup>1,2,3</sup>, Wenchao Yang<sup>3</sup>, Ju Tao<sup>3</sup>, Qianlei Wang<sup>1,2</sup>, Zhe Cui<sup>1,2</sup>, and Xiaolin Qin<sup>1,2</sup>

**Affiliations:**

<sup>1</sup> Chengdu Institute of Computer Applications, Chinese Academy of Sciences, Chengdu, Sichuan 610041, China (e-mail: yale.li.cn@gmail.com).

<sup>2</sup> University of Chinese Academy of Sciences, Beijing 100049, China.

<sup>3</sup> Jiayu Intelligent Technology Co.,Ltd. (Affiliated With Great Wall Motor Company Limited).


## Introduction

This is the website for our paper "[AVM-SLAM: Semantic Visual SLAM with Multi-Sensor Fusion in a Bird’s Eye View for Automated Valet Parking](https://arxiv.org/abs/2309.08180)", Submitted to ICRA2024 for review.

Automated Valet Parking (AVP) requires precise localization in challenging garage conditions, including poor lighting, sparse textures, repetitive structures, dynamic scenes, and the absence of Global Positioning System (GPS) signals, which often pose problems for conventional localization methods. To address these adversities, we present AVM-SLAM, a semantic visual SLAM framework with multi-sensor fusion in a Bird's Eye View (BEV). Our framework integrates four fisheye cameras, four wheel encoders, and an Inertial Measurement Unit (IMU). The fisheye cameras form an Around View Monitor (AVM) subsystem, generating BEV images. Convolutional Neural Networks (CNNs) extract semantic features from these images, aiding in mapping and localization tasks. These semantic features provide long-term stability and perspective invariance, effectively mitigating environmental challenges. Additionally, data fusion from wheel encoders and IMU enhances system robustness by improving motion estimation and reducing drift.

## Framework

![AVM-SLAM Framework](https://github.com/yale-cv/avm-slam/blob/main/img/framework.jpg)

This paper introduces the AVM-SLAM system, consisting of two core modules: VIWFusion and Mapping. Our design utilizes a unique multi-sensor hybrid fusion strategy, departing from traditional approaches, ensuring seamless collaboration between these modules for maximum multi-sensor fusion benefits.

- **VIWFusion**: A loosely-coupled, multi-sensor weighted fusion front-end encompassing the AVM subsystem, Semantic Extractor, Matcher, IMU Tracker, Wheel Odometry, Pose Predictor, and Keyframe Filter. It applies weighted fusion to data from surround cameras, wheel encoders, and IMU sensors, rooted in Extended Kalman Filter (EKF) theory, providing initial values for visual semantic matching and kinematic constraints for subsequent back-end optimization through pre-integrated values among adjacent semantic keyframes (IMU and wheel).

- **Mapping**: A tightly-coupled, semantic mapping back-end, comprising the Loop Detector, Global Optimizer, Sub Mapper, and Global Mapper. We utilize semantic ICP registration for loop detection, incorporating a semantic pre-qualification (SPQ) mechanism to streamline loop detection and minimize mismatches. Extra multi-sensor kinematic constraints, like pre-integrated values of IMU and Wheel between adjacent keyframes, expedite global optimization convergence and enhance mapping accuracy.

## Experiments

![Experiments Details](https://github.com/yale-cv/avm-slam/blob/main/img/fig9a.jpg)

![Experiments Details](https://github.com/yale-cv/avm-slam/blob/main/img/fig9b.jpg)

We performed a qualitative analysis using a schematic map of the planar structure of the garage (as shown in Fig. 9a) with the semantic map we constructed. The two are made to have the same size by scaling and are overlapped for comparison, as shown in Fig. 9b. Obviously, the semantic map built by our system can be perfectly aligned with the schematic map of the garage, with very high mapping accuracy.

![Experiments Details](https://github.com/yale-cv/avm-slam/blob/main/img/experiments.png)

We conducted a quantitative analysis by comparing the world distances between the six points, denoted as ABCDEF in Fig.9a, with the corresponding map distances. The world distances were measured using a high-precision laser rangefinder, while the map distances were computed from the respective 3D point coordinates. Table I presents the mean values of multiple measurements for both world distances and map distances. Table II shows the mean absolute error, maximum error, and root mean square error (RMSE) between these map distances and world distances, and attaches experimental data from the AVP-SLAM [22] and BEV Edge SLAM [24] for comparison. It should be noted that the authors of these two methods have not open-sourced them, so the data in the table are derived from the literature. Although the datasets are different, the application scenarios of the three methods are all underground garage, so they can still be used as references to each other. From Table II, it is obvious that ours AVM-SLAM system fusing multi-sensors has a higher accuracy of mapping.

## Dataset

![Dateset Infomation](https://github.com/yale-cv/avm-slam/blob/main/img/information.png)

To validate the proposed AVM-SLAM system, tests were conducted in a 220m×110m underground garage with over 430 parking spots using a test vehicle equipped with four surround-view fisheye cameras, four wheel encoders, and an IMU, all synchronized and calibrated offline.

The dataset encompasses:
- Four fisheye image sequences (10Hz@1280x960)
- One Bird's Eye View (BEV) image sequence (10Hz@1354x1632, 1.05cm/pixel) generated by our Around View Monitor (AVM) subsystem
- Four sets of wheel encoder data
- One IMU dataset

This dataset will be beneficial for further research in SLAM, especially for autonomous vehicle localization in underground garages. For access to the dataset, please contact the authors for details.

This dataset is only for academeic use under the GNU General Public License Version 3 (GPLv3). For commercial purposes, please contact the authors for details.