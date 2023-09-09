# AVM-SLAM: Semantic Visual SLAM with Multi-Sensor Fusion in a Bird’s Eye View for Automated Valet Parking

**Authors:** Ye Li^1,2,3^, Wenchao Yang^3^, Ju Tao^3^, Qianlei Wang^1,2^, Zhe Cui^1,2^, and Xiaolin Qin^1,2^

**Affiliations:**

^1^ Chengdu Institute of Computer Applications, Chinese Academy of Sciences, Chengdu, Sichuan 610041, China (e-mail: yale.li.cn@gmail.com).

^2^ University of Chinese Academy of Sciences, Beijing 100049, China.

^3^ Jiayu Intelligent Technology Co.,Ltd. (Affiliated With Great Wall Motor Company Limited).


## Introduction

This is the website for our paper "AVM-SLAM: Semantic Visual SLAM with Multi-Sensor Fusion in a Bird’s Eye View for Automated Valet Parking", ICRA 2024.


## Framework

![AVM-SLAM Framework](insert_framework_image_url_here)



## Experiments

![Experiments Details](insert_comparison_image_url_here)



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