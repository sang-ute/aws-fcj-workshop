+++
title = "Clean up resources"
date = 2022
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

We will take the following steps to delete the resources we created in this exercise.

#### Delete Rekognition resources

AWS Rekognition resources cannot be deleted from the AWS Management Console.  
You must delete them using the AWS CLI or by writing code that calls the appropriate Rekognition API.

1. **Delete Face Collections**
   ```bash
   aws rekognition delete-collection --collection-id <collection-id>
   ```

#### Delete S3 bucket

#### Remove Amplify project

1. In your local project folder, run:
   ```bash
   amplify delete
   Type Y to confirm.
   ```

This will remove the backend environment and all associated Amplify-managed resources.

#### Delete VPC Endpoints

1. Go to [VPC service management console](https://console.aws.amazon.com/vpc/home)
   - Click **Endpoints**.
   - Select the 4 endpoints we created for the lab including **SSM**, **SSMMESSAGES**, **EC2MESSAGES**, **S3GW**.
   - Click **Actions**.
   - Click **Delete VPC endpoints**.

![Clean](/images/6.clean/004-clean.png)

2. In the confirm box, enter **delete**.

   - Click **Delete** to proceed with deleting endpoints.

3. Click the refresh icon, check that all endpoints have been deleted before proceeding to the next step.

![Clean](/images/6.clean/005-clean.png)

#### Delete VPC

1. Go to [VPC service management console](https://console.aws.amazon.com/vpc/home)

   - Click **Your VPCs**.
   - Click on **Lab VPC**.
   - Click **Actions**.
   - Click **Delete VPC**.

2. In the confirm box, enter **delete** to confirm, click **Delete** to delete **Lab VPC** and related resources.

![Clean](/images/6.clean/006-clean.png)
