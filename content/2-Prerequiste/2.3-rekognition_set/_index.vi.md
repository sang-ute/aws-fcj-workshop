---
title: "Tạo collection Rekognition thông qua CLI"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

## Tạo collection Rekognition

Để lưu trữ và quản lý các khuôn mặt được lập chỉ mục, trước tiên bạn cần tạo một **collection** trong Amazon Rekognition.

Chạy lệnh sau, thay thế `my-face-collection` bằng tên collection bạn mong muốn:

```bash
aws rekognition create-collection --collection-id my-face-collection
```

Nếu thành công, bạn sẽ thấy kết quả tương tự như sau:

```bash
{
"StatusCode": 200,
"CollectionArn": "arn:aws:rekognition:us-east-1:123456789012:collection/my-face-collection",
"FaceModelVersion": "6.0"
}
```

{{% notice tip %}}
Hãy đảm bảo AWS CLI của bạn đã được cấu hình với hồ sơ và khu vực chính xác trước khi chạy lệnh này. Bạn có thể chỉ định chúng một cách rõ ràng nếu cần:
{{% /notice %}}

```bash
aws rekognition create-collection --collection-id my-face-collection --profile my-profile --region us-east-1
```
