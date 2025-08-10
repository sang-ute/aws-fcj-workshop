---
title: "Setup for AWS CLI"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Configure AWS credentials

Before you can deploy any resources, make sure your AWS CLI is set up with valid credentials.  
{{% notice info %}}
For a detailed walkthrough, see [Lab 000011. Getting Started with the AWS CLI](https://000011.awsstudygroup.com/).
{{% /notice %}}
If you haven’t done this yet, run:

```bash
aws configure
```

The CLI will ask for your Access Key ID, Secret Access Key, default region, and output format.
Some example for setting up:
Create an AWS Account: If you don’t already have an AWS account, sign up here. An AWS account is required to complete this exercise.

Here's how to create an IAM user and set up your AWS CLI:

### Create an IAM Group:

- Log in to your AWS Management Console.
- Navigate to the IAM (Identity and Access Management) service.
- Create a new IAM group, assign a name, and define the necessary permissions for your use case (in this case for convinience, you should select "AdministatorAccess" for this profile, or configure later in my workshop).
- Create an IAM User:

Still within the IAM service, create a new IAM user.

- Assign this user to the IAM group you just created.
- Take note of the Access Key ID and Secret Access Key for future use.
- Generate AWS Access Keys:

Select the IAM user you created.

- Under the Security Credentials tab, generate a new pair of access keys.
- Safely store the Access Key ID and Secret Access Key—you will need them to authenticate with AWS services.

```bash
aws configure
AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
Default region name [None]: us-east-1
Default output format [None]: json
```

{{% notice warning %}}
Remember to set region to `us-east-1` or to these region (since Amplify and Rekognition Liveness is only available in these regions only)
| Region Name | Region Code |
| ------------------------- | ---------------- |
| **US East (N. Virginia)** | `us-east-1` |
| **US West (Oregon)** | `us-west-2` |
| **Europe (Ireland)** | `eu-west-1` |
| **Asia Pacific (Tokyo)** | `ap-northeast-1` |
| **Asia Pacific (Mumbai)** | `ap-south-1` |

{{% /notice %}}

If you prefer to work with a named profile (which has one of those region above), set it as your active profile:

### macOS / Linux

```
export AWS_PROFILE=my-profile
```

### Windows PowerShell

```
$env:AWS_PROFILE = "my-profile"
```

### Windows CMD

```
set AWS_PROFILE=my-profile
```
