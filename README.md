# Marine Mechatronics: Visual Servoing

**University of Toulon**  
August 12, 2024

**Authors:**  
Sergei Chashnikov  
Abhimanyu Bhowmik  
Madhushree Sannigrahi  
Tayyab Tahir  
Ishfaq Bhat

**Supervisors:**  
Prof. Claire Dune  
Prof. Vincent Hugel

## Overview

This project focuses on implementing visual servoing for underwater robotics, specifically using a BlueROV to track and control an orange buoy. The project integrates image-based visual servoing (IBVS) with a proportional (P) controller to manage various degrees of freedom in the BlueROV. The objective is to enhance the accuracy and efficiency of underwater navigation and object tracking.

## Contents

1. [Introduction](#introduction)
2. [Image-Based Visual Servoing Control (IBVS)](#image-based-visual-servoing-control-ibvs)
3. [Methodology](#methodology)
   - [System Setup and Configuration](#system-setup-and-configuration)
     - [Setting up the autonomous rov Package](#setting-up-the-autonomous-rov-package)
     - [Calibration and Parameter Adjustment](#calibration-and-parameter-adjustment)
   - [Feature Detection and Tracking](#feature-detection-and-tracking)
     - [Conversion to HSV Color Space](#conversion-to-hsv-color-space)
     - [Color Masking](#color-masking)
     - [Contour Detection](#contour-detection)
     - [Centroid Calculation](#centroid-calculation)
   - [Interaction Matrix Computation](#interaction-matrix-computation)
     - [Degrees of Freedom Management](#degrees-of-freedom-management)
   - [Control System Implementation](#control-system-implementation)
     - [Proportional Controller](#proportional-controller)
     - [Frame Transformation and Real-time Application](#frame-transformation-and-real-time-application)
   - [ROS Integration and Velocity Broadcasting](#ros-integration-and-velocity-broadcasting)
4. [Results and Discussion](#results-and-discussion)
   - [System Responsiveness on Bag Files](#system-responsiveness-on-bag-files)
   - [Preliminary Tests with the BlueROV](#preliminary-tests-with-the-bluerov)
   - [Yaw-Heave Control](#yaw-heave-control)
   - [Sway-Heave Control](#sway-heave-control)
   - [5-Degrees of Freedom Control](#5-degrees-of-freedom-control)

## Introduction

Visual servoing integrates computer vision techniques with robotic control, enabling precise navigation and object detection in dynamic environments. This project implements visual servoing using OpenCV to track an orange buoy and applies a proportional controller to control the BlueROV across various degrees of freedom.

## Image-Based Visual Servoing Control (IBVS)

Visual servoing minimizes the error between the desired and actual positions of a feature point in an image. This project utilizes the interaction matrix (Ls) to compute the necessary camera velocities to reduce this error.

## Methodology

### System Setup and Configuration

1. **Setting up the autonomous rov Package:**
   - Install ROS and configure the Catkin workspace.
   - Add image processing, tracking, and control code to the autonomous rov package.

2. **Calibration and Parameter Adjustment:**
   - Calibrate the camera and adjust HSV thresholds for buoy detection.

### Feature Detection and Tracking

1. **Conversion to HSV Color Space:**
   - Convert images to HSV color space for better color segmentation.

2. **Color Masking:**
   - Apply a binary mask to isolate the buoy based on HSV values.

3. **Contour Detection:**
   - Detect contours in the binary mask to identify the buoy’s boundaries.

4. **Centroid Calculation:**
   - Compute the centroid of the largest contour to determine the buoy’s position.

### Interaction Matrix Computation

Compute the interaction matrix (L) for the visual servoing system, considering different methods for estimating the matrix and managing degrees of freedom.

#### Degrees of Freedom Management

Test and manage degrees of freedom (yaw, heave, sway) to streamline the control process.

### Control System Implementation

1. **Proportional Controller:**
   - Implement a proportional controller to adjust the BlueROV’s motion based on the error.

2. **Frame Transformation and Real-time Application:**
   - Transform camera velocities to the BlueROV’s body frame and apply them in real-time.

### ROS Integration and Velocity Broadcasting

Integrate the system with ROS for communication and data transmission, publishing topics for camera velocity, robot velocity, and visual servoing error.

## Results and Discussion

### System Responsiveness on Bag Files

The buoy recognition algorithm was tested with bag files and demonstrated accurate detection and tracking.

### Preliminary Tests with the BlueROV

Initial tests on the BlueROV in an air environment identified and resolved bugs in the control system.

### Yaw-Heave Control

Evaluated the controller’s performance for yaw and heave control, demonstrating effective error reduction with observable oscillations.

### Sway-Heave Control

Assessed sway and heave control with observed immediate error reduction and stability issues.

### 5-Degrees of Freedom Control

Tested the controller with five degrees of freedom, achieving error reduction with some residual jitter.

## Figures

1. RGB Image with track point and desired point overlay; Image in HSV format; Contour mask for the buoy.
2. Degrees of Freedom of a BlueROV.
3. ROS Node structures.
4. Orange buoy in the bag file; Color mask along with the current and desired point.
5. Yaw-Heave Control.
6. Sway-Heave Control.
7. 5-Degrees Control.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

Special thanks to Prof. Claire Dune and Prof. Vincent Hugel for their guidance and support throughout this project.

---

For further details, visit our [GitHub repository](https://github.com/Ishfaz/Visual-Servoing).

