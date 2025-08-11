---
title: "Preparation "
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice info %}}
This lab will introduce 2 ways of practice, 1 is to deploy locally, the other is to deploy to AWS as a serverless application.
{{% /notice %}}

To learn how to create a serverless application with ease, you should do these the labs first:

- [About Amazon S3](https://000057.awsstudygroup.com/) (note that you only need to learn how to create a simple bucket and cleanup)
- [Learn how to host static website](https://000094.awsstudygroup.com/) (you need to build dist folder and upload to S3)
- [Learn how to build a serverless website](https://000078.awsstudygroup.com/) (this is the lab to learn how to work with API Gateway and Lambda for serverless application)

If you want just to deploy this app locally (but would work otherwise to the whole system, then these labs won't be needed much)

### Content

- [Installing Node.js enviroment and system](2.1-installing_env/)
- [Installing npm and AWS CLI (with Amplify CLI)](2.2-setup_awscli/)
- [Create Rekognition collection set](2.3-rekognition_set/)
