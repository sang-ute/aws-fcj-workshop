---
title: "Face attendance with anti-spoofing using AWS Rekognition FaceLiveness, CompareFaces and SearchFacesByImage via Amplify"
date: "`r Sys.Date()`"
weight: 1
chapter: false
---

# Face Attendance System with AWS Rekognition and Amplify

### Overview

This lab introduces a face attendance system that combines **AWS Rekognition** and **Amplify** to verify user identity using real-time face liveness detection and face matching.  
The system eliminates spoofing by requiring a live user presence before matching their face against a stored collection.

The core flow includes:

- **Liveness check** using `FaceLivenessDetector`
- **Face matching** using `CompareFaces` and `SearchFacesByImage`
- **Frontend** built with React and Amplify
- **Backend** using Express and AWS SDK

![ConnectPrivate](/images/arc-log.png)

### Content

1. [Introduction](1-introduce/)  
   Overview of the project goal, architecture, and Rekognition features used.

2. [Preparation](2-prerequiste/)  
   Set up both your development and AWS environments:

   - Install **Node.js** and **npm**
   - Install and configure the **AWS CLI** (`aws configure`)
   - Install the **Amplify CLI** (`npm install -g @aws-amplify/cli`)
   - Bootstrap your React frontend (`npx create-react-app`)
   - Initialize Amplify (`amplify init`)
   - Enable **Face Liveness** in Amplify
   - Create a **Rekognition collection**, **S3 bucket**, and required **IAM roles**

3. [Liveness Detection with Amplify](3-liveness/)  
   Integrate `FaceLivenessDetector` to capture live user sessions in the browser.

4. [Face Matching Logic](4-matching/)  
   Process the captured image and match it against the Rekognition collection using `CompareFaces` or `SearchFacesByImage`.

5. [Attendance Check-In Flow](5-checkin/)  
   Build the complete check-in logic: from frontend liveness → to backend match → to recording attendance (e.g., in DynamoDB).

6. [Clean Up Resources](6-cleanup/)  
   Remove all AWS and local resources to avoid incurring costs.
