---
title: "Clean up resources"
date: "`r Sys.Date()`"
weight: 9
chapter: false
pre: " <b> 9. </b> "
---

### **Clean Up Resources**

We will take the following steps to delete the resources we created in this exercise.

---

#### **Delete Rekognition Resources**

AWS Rekognition resources cannot be deleted from the AWS Management Console.
You must delete them using the AWS CLI or by writing code that calls the appropriate Rekognition API.

1. **Delete Face Collections**

   ```bash
   aws rekognition delete-collection --collection-id <collection-id>
   ```

---

#### **Delete S3 Buckets**

1. Go to **S3 service console**.
2. Select the buckets you created for:

   - Storing face images
   - Hosting the frontend
   - Any temporary data storage

3. Click **Empty** (to remove all objects), then **Delete**.
4. Confirm bucket name when prompted.

---

#### **Remove Amplify Project**

From your local project folder:

```bash
amplify delete
```

- Type **Y** to confirm.
  This will remove the backend environment and all associated Amplify-managed resources.

---

#### **Delete Lambda Functions**

1. Go to **Lambda service console**.
2. Select all functions created for:

   - `sessionFunction`
   - `livenessResultFunction`
   - `indexFaceFunction`
   - `listCollectionFunction`
   - `deleteFaceFunction`
   - `attendanceFunction`

3. Click **Actions → Delete**.

---

#### **Delete API Gateway Endpoints**

1. Go to **API Gateway console**.
2. Select the REST APIs you created.
3. Click **Actions → Delete**.
4. Confirm deletion.

---

#### **Delete CloudFront Distributions**

1. Go to **CloudFront console**.
2. Select the distribution(s) you created.
3. Click **Disable**, wait until status is **Disabled**.
4. Click **Delete** and confirm.

---

#### **Delete CloudWatch Logs**

1. Go to **CloudWatch console**.
2. Select **Log groups**.
3. Delete all log groups created for your Lambda functions and API Gateway.

---

#### **Delete DynamoDB Tables** _(if created)_

1. Go to **DynamoDB console**.
2. Select any tables created for session storage or attendance tracking.
3. Click **Delete table**, confirm name.
