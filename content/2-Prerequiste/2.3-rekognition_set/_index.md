---
title: "Create Rekognition collection set via CLI"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

## Create a Rekognition Collection

To store and manage indexed faces, you’ll first need to create a **collection** in Amazon Rekognition.

Run the following command, replacing `my-face-collection` with your desired collection name:

```bash
aws rekognition create-collection --collection-id my-face-collection
```

If successful, you’ll see output similar to:

```bash
{
"StatusCode": 200,
"CollectionArn": "arn:aws:rekognition:us-east-1:123456789012:collection/my-face-collection",
"FaceModelVersion": "6.0"
}
```

{{% notice tip %}}
Make sure your AWS CLI is configured with the correct profile and region before running this command. You can specify them explicitly if needed:
{{% /notice %}}

```bash
aws rekognition create-collection --collection-id my-face-collection --profile my-profile --region us-east-1
```
