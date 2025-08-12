---
title: "Thiết lập bucket S3"
date: "`r Sys.Date()`"
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

## TẠO VÀ CẤU HÌNH bucket S3

### 1. **Tạo bucket S3**

Truy cập: https://s3.console.aws.amazon.com/s3/home

![alt text](image-1.png)

Nhấn **Tạo bucket**, và điền thông tin:

### ▸ **Khu vực AWS**:

- Chọn khu vực ưu tiên (giống với trong **hồ sơ AWS** của bạn), ví dụ: `us-east-1`  
  ![alt text](image-3.png)

  {{% notice info %}}
  Nếu bạn sử dụng một khu vực AWS khác, bạn cần cập nhật khu vực trong Bảng điều khiển quản lý AWS ở góc trên bên phải, bên cạnh ID tài khoản.
  {{% /notice %}}

### ▸ **Loại bucket**:

- Chọn "Mục đích chung"

### ▸ **Tên bucket**:

- Sử dụng chữ thường, không có khoảng trắng.
- Ví dụ: `face-recognition-users`
- Ghi nhớ tên bucket.

![alt text](image.png)

### 2. **Quyền sở hữu đối tượng**

Điều này ảnh hưởng đến việc liệu các đối tượng được tải lên bởi người khác có thuộc sở hữu của bạn (chủ sở hữu bucket) hay không.

**Cài đặt đề xuất**:

- Chọn: **Tắt ACLs** (Chủ sở hữu bucket được áp dụng) → an toàn nhất và được ưu tiên.
- Lý do: Ngăn chặn các vấn đề liên tài khoản và đảm bảo chủ sở hữu bucket sở hữu tất cả các tệp được tải lên.

---

![alt text](image-2.png)

### 3. **Cài đặt chặn truy cập công khai**

Điều này quyết định liệu các đối tượng có thể được công khai hay không.

**Cài đặt đề xuất** (DÀNH CHO DỮ LIỆU KHUÔN MẶT RIÊNG TƯ):

- Giữ tất cả **4 hộp kiểm được chọn** (mặc định):
  - Chặn toàn bộ truy cập công khai
  - Chặn ACLs công khai
  - Chặn chính sách bucket công khai
  - Hạn chế bucket công khai

📌 Lý do? Bạn **không** muốn bất kỳ ai từ internet truy cập vào hình ảnh khuôn mặt người dùng.

![alt text](image-4.png)

> Nếu thử nghiệm yêu cầu truy cập công khai tạm thời, bạn có thể bỏ chặn sau, nhưng luôn kích hoạt lại cho môi trường sản xuất.

---

### 4. **Phiên bản hóa bucket**

Tính năng này lưu trữ nhiều phiên bản của cùng một tệp.

- **Đề xuất**: **Tắt**
- Trừ khi bạn cần theo dõi các thay đổi hoặc xóa, phiên bản hóa là không cần thiết và tốn chi phí hơn.

![alt text](image-5.png)

---

### 5. **Mã hóa mặc định**

Mã hóa các đối tượng khi lưu trữ.

![alt text](image-6.png)

**Đề xuất**: **Kích hoạt**

- Chọn: **Khóa do S3 quản lý (SSE-S3)** → đơn giản nhất và vẫn an toàn
- Hoặc, để kiểm soát nhiều hơn: **Khóa AWS KMS (SSE-KMS)** → cho các môi trường được quy định

📌 Mã hóa giúp bảo vệ dữ liệu khuôn mặt nhạy cảm.

---

### 6. **Cài đặt nâng cao**

Bạn có thể bỏ qua hầu hết các cài đặt này trừ khi cần ghi nhật ký hoặc sao chép.  
**Thẻ**: Không cần thiết lúc này (tùy chọn cho việc theo dõi chi phí)

![alt text](image-7.png)

**Khóa đối tượng**: Giữ tắt trừ khi bạn cần WORM (ghi một lần, đọc nhiều lần)

![alt text](image-8.png)

Bước cuối: Tạo bucket

Nhấn **"Tạo bucket"** để hoàn tất.

![alt text](image-9.png)

---

### Kiểm tra sau thiết lập

1. **Tab Quyền**:
   - Đảm bảo **"Chặn toàn bộ truy cập công khai"** vẫn được kích hoạt.

![alt text](image-10.png)

2. **Tab Thuộc tính**:
   - Xác nhận mã hóa và khu vực là chính xác.

![alt text](image-11.png)

![alt text](image-12.png)

3. **Tải lên tệp thử nghiệm** (tùy chọn):
   - Tải lên một hình ảnh khuôn mặt vào thư mục `faces/` (tùy chọn tổ chức).

---

### Tóm tắt cho trường hợp sử dụng Rekognition khuôn mặt

| Cài đặt                 | Giá trị                                   |
| ----------------------- | ----------------------------------------- |
| Quyền sở hữu đối tượng  | Chủ sở hữu bucket được áp dụng (Tắt ACLs) |
| Chặn truy cập công khai | Tất cả được chọn                          |
| Phiên bản hóa           | Tắt                                       |
| Mã hóa                  | SSE-S3                                    |
| Tên bucket              | your_s3_name                              |
| Thư mục (tùy chọn)      | faces/                                    |

## BƯỚC 2: Thiết lập `.env`

Tạo một tệp `.env` trong thư mục dự án của bạn (hoặc sử dụng như tệp .env.example trong dự án sao chép của hội thảo này, các biến môi trường khác như Dynamo có thể được xây dựng sau trong hội thảo):

```
AWS_REGION=us-east-1 #hoặc khu vực bạn đã chọn
S3_BUCKET=your-bucket-name
REKOGNITION_COLLECTION=your-collection-name
```
