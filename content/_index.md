---
title: "Face attendance with anti-spoofing using AWS Rekognition, via Amplify"
date: "`r Sys.Date()`"
weight: 1
chapter: false
---

# Face attendance with anti-spoofing using AWS Rekognition, via Amplify

### Overview

This lab introduces a face attendance system that combines **AWS Rekognition** and **Amplify** to verify user identity using real-time face liveness detection and face matching.  
The system eliminates spoofing by requiring a live user presence before matching their face against a stored collection.

The core flow includes:

- **Liveness check** using `FaceLivenessDetector`
- **Face matching** using `CompareFaces` and `SearchFacesByImage`
- **Frontend** built with React and Amplify
- **Backend** using Express and AWS SDK

Here's the architechture of a live session (when deploying serverless)

![alt text](image.png)

### Content

1. Overview of the project goal, architecture, and Rekognition features used.

2. Set up both your development and AWS environments:

   - Install **Node.js** and **npm**
   - Install and configure the **AWS CLI** (`aws configure`)
   - Install the **Amplify CLI** (`npm install -g @aws-amplify/cli`)
   - Initialize Amplify (`amplify init`)
   - Enable **Face Liveness** in Amplify
   - Create a **Rekognition collection**, **S3 bucket**, and required **IAM roles**

3. Integrate Amplify to capture live user sessions in the browser.

4. Create and setup correct S3 for Rekognition to connect

5. Build the complete check-in logic: from frontend liveness → to backend match → to recording attendance (e.g., in DynamoDB).

6. Deploy locally, then to Amplify for serverless deployment.

7. Deploy the Lambda functions to API Gateway to expose them as REST APIs.

8. Deploy the frontend to S3 + CloudFront Hosting.

9. Clean up resources to avoid unnecessary costs.
