---
title: "Dọn dẹp tài nguyên"
date: "`r Sys.Date()`"
weight: 9
chapter: false
pre: " <b> 9. </b> "
---

### **Dọn dẹp tài nguyên**

Chúng ta sẽ thực hiện các bước sau để xóa các tài nguyên đã tạo trong bài tập này.

---

#### **Xóa tài nguyên Rekognition**

Tài nguyên AWS Rekognition không thể xóa từ AWS Management Console.
Bạn phải xóa chúng bằng AWS CLI hoặc bằng cách viết mã gọi API Rekognition phù hợp.

1. **Xóa Face Collections**

   ```bash
   aws rekognition delete-collection --collection-id <collection-id>
   ```

---

#### **Xóa S3 Buckets**

1. Truy cập **S3 service console**.
2. Chọn các bucket bạn đã tạo cho:

   - Lưu trữ hình ảnh khuôn mặt
   - Lưu trữ frontend
   - Bất kỳ lưu trữ dữ liệu tạm thời nào

3. Nhấp **Empty** (để xóa tất cả các đối tượng), sau đó nhấp **Delete**.
4. Xác nhận tên bucket khi được yêu cầu.

---

#### **Xóa dự án Amplify**

Từ thư mục dự án cục bộ của bạn:

```bash
amplify delete
```

- Nhập **Y** để xác nhận.
  Thao tác này sẽ xóa môi trường backend và tất cả các tài nguyên do Amplify quản lý.

---

#### **Xóa Lambda Functions**

1. Truy cập **Lambda service console**.
2. Chọn tất cả các hàm được tạo cho:

   - `sessionFunction`
   - `livenessResultFunction`
   - `indexFaceFunction`
   - `listCollectionFunction`
   - `deleteFaceFunction`
   - `attendanceFunction`

3. Nhấp **Actions → Delete**.

---

#### **Xóa API Gateway Endpoints**

1. Truy cập **API Gateway console**.
2. Chọn các REST APIs bạn đã tạo.
3. Nhấp **Actions → Delete**.
4. Xác nhận xóa.

---

#### **Xóa CloudFront Distributions**

1. Truy cập **CloudFront console**.
2. Chọn (các) distribution bạn đã tạo.
3. Nhấp **Disable**, đợi cho đến khi trạng thái là **Disabled**.
4. Nhấp **Delete** và xác nhận.

---

#### **Xóa CloudWatch Logs**

1. Truy cập **CloudWatch console**.
2. Chọn **Log groups**.
3. Xóa tất cả các log groups được tạo cho Lambda functions và API Gateway của bạn.

---

#### **Xóa DynamoDB Tables** _(nếu đã tạo)_

1. Truy cập **DynamoDB console**.
2. Chọn bất kỳ bảng nào được tạo để lưu trữ phiên hoặc theo dõi điểm danh.
3. Nhấp **Delete table**, xác nhận tên.
