---
title: "Chuẩn bị"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice info %}}
Bài lab này sẽ trình bày hai phương pháp thực hành: một là triển khai cục bộ, hai là triển khai lên AWS dưới dạng ứng dụng không máy chủ.
{{% /notice %}}

Để nắm vững cách tạo một ứng dụng không máy chủ một cách hiệu quả, bạn nên hoàn thành các bài lab sau trước:

- [Về Amazon S3](https://000057.awsstudygroup.com/) (lưu ý rằng bạn chỉ cần tìm hiểu cách tạo một bucket S3 đơn giản và thực hiện dọn dẹp)
- [Tìm hiểu cách lưu trữ trang web tĩnh](https://000094.awsstudygroup.com/) (bạn cần xây dựng thư mục dist và tải lên S3)
- [Tìm hiểu cách xây dựng một trang web không máy chủ](https://000078.awsstudygroup.com/) (đây là bài lab để tìm hiểu cách làm việc với API Gateway và Lambda cho ứng dụng không máy chủ)

Nếu bạn chỉ muốn triển khai ứng dụng này cục bộ (nhưng vẫn hoạt động tương thích với toàn bộ hệ thống), các bài lab trên không cần thiết quá nhiều.

### Nội dung

- [Cài đặt môi trường và hệ thống Node.js](2.1-installing_env/)
- [Cài đặt npm và AWS CLI (kèm theo Amplify CLI)](2.2-setup_awscli/)
- [Tạo collection Rekognition](2.3-rekognition_set/)
