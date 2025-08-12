---
title: "Triển khai S3 UI Bucket và CloudFront CDN"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 8. </b> "
---

## **Triển khai Frontend React/Vite đến S3 + CloudFront**

---

### **Bước 1 — Tạo S3 Bucket**

1. Truy cập **AWS Console → S3 → Create bucket**.
2. **Bucket name:**
   Đặt một **tên duy nhất** (ví dụ: `my-frontend-app-bucket`).
   _(Đây là trường duy nhất bạn thay đổi — giữ tất cả các cài đặt khác ở mặc định.)_

   ![alt text](image.png)

3. Để nguyên:

   - AWS Region → Mặc định hoặc tùy chọn của bạn
   - Object Ownership → ACLs disabled
   - Block Public Access → Giữ mặc định
   - Versioning, Encryption, Tags → mặc định

![alt text](image-1.png)

4. Nhấp **Create bucket**.

![alt text](image-2.png)

---

### **Bước 2 — Tạo CloudFront Distribution**

1. Truy cập **AWS Console → CloudFront → Create distribution**.

![alt text](image-3.png)

Sau đó nhập tên Distribution của bạn

![alt text](image-4.png)

2. **Origin type:** Chọn **S3**.

![alt text](image-5.png)

3. Chọn S3 bucket bạn vừa tạo.

![alt text](image-6.png)

4. Giữ **tất cả các cài đặt khác ở mặc định**:

![alt text](image-8.png)

- Viewer protocol policy → Redirect HTTP to HTTPS
- Cache settings → Use origin cache headers
- Logging → Off

5. Nhấp **Next**.
6. **Web Application Firewall (WAF):** Chọn **Do not enable**.

![alt text](image-9.png)

7. Nhấp **Next**.
8. Xem lại → Nhấp **Create distribution**.

![alt text](image-7.png)

---

### **Bước 3 — Thiết lập Default Root Object**

1. Truy cập CloudFront distribution mới của bạn.
2. **Settings → Edit**.

![alt text](image-10.png)

3. **Default root object:** `index.html`

![alt text](image-11.png)

4. Lưu thay đổi.

---

### **Bước 4 — Build Frontend của Bạn**

Từ dự án cục bộ của bạn:

```bash
cd frontend
npm run build
```

Điều này sẽ tạo ra đầu ra build trong thư mục `dist/` (Vite) hoặc `build/` (React).

![alt text](image-12.png)

---

### **Bước 5 — Tải lên S3**

1. Sao chép mọi thứ bên trong thư mục `dist/` (không phải chính thư mục đó).
2. Truy cập **S3 bucket → Upload**.

![alt text](image-13.png)

3. Kéo và thả các file, giữ nguyên quyền mặc định, nhấp **Upload**.

---

### **Bước 6 — Chờ CloudFront Propagation**

- Có thể mất **vài phút** để CloudFront cập nhật.

![alt text](image-14.png)

- Khi hoàn tất, truy cập **CloudFront → Your Distribution → Copy the Distribution Domain Name** (không phải ARN).

![alt text](image-15.png)

- Dán vào trình duyệt của bạn để truy cập trang web.

![alt text](image-16.png)

Và thế là xong! Bạn đã thiết lập thành công một frontend serverless với Vite và triển khai nó lên AWS bằng CloudFront và S3. Bây giờ bạn có thể xem trang web của mình cập nhật trong thời gian thực khi bạn thực hiện các thay đổi trong mã. Chúc bạn coding vui vẻ với AWS, và cảm ơn bạn rất nhiều vì đã tham gia workshop này cho đến bây giờ!
