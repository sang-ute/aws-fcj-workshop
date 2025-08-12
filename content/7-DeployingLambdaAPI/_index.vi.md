---
title: "Triển khai hàm Lambda và API Gateway"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

### Giới thiệu

Khi xây dựng các ứng dụng hiện đại, **kiến trúc serverless** cho phép bạn tập trung hoàn toàn vào việc viết mã trong khi nhà cung cấp đám mây quản lý hạ tầng.  
Trong AWS, hai dịch vụ chính giúp điều này trở nên khả thi:

- **Amazon API Gateway** – Dịch vụ được quản lý hoàn toàn để tạo, xuất bản và bảo mật API ở quy mô lớn.
- **AWS Lambda** – Dịch vụ tính toán chạy mã của bạn theo yêu cầu, không cần cung cấp hay quản lý máy chủ.

Kết hợp lại, chúng cho phép tạo ra **API serverless** nơi các yêu cầu được định tuyến qua API Gateway và xử lý bởi các hàm Lambda.

---

### Tại sao chọn Serverless?

Với các ứng dụng truyền thống, bạn phải:

- Cung cấp máy chủ.
- Bảo trì hệ điều hành.
- Xử lý khả năng mở rộng và chuyển đổi dự phòng.
- Trả tiền cho dung lượng nhàn rỗi.

Với API Gateway + Lambda:

- **Không cần bảo trì máy chủ** – AWS chạy hạ tầng tính toán cho bạn.
- **Tự động mở rộng** – Mã của bạn tự động mở rộng và thu hẹp theo số lượng yêu cầu.
- **Trả tiền theo lần chạy** – Bạn chỉ trả tiền khi mã chạy.
- **Triển khai nhanh chóng** – Đưa tính năng mới vào mà không phải động đến hạ tầng.

---

### Cách hoạt động

1. **Khách hàng gửi yêu cầu**  
   Người dùng hoặc ứng dụng gửi một yêu cầu HTTP đến endpoint API Gateway của bạn.

2. **API Gateway định tuyến yêu cầu**  
   API Gateway khớp yêu cầu với một route đã cấu hình và chuyển đến hàm AWS Lambda tương ứng.

3. **Lambda thực thi logic nghiệp vụ**  
   Hàm Lambda xử lý yêu cầu — như đọc dữ liệu từ DynamoDB, gọi API khác, hoặc chạy suy luận AI — rồi trả về phản hồi.

4. **API Gateway gửi phản hồi lại**  
   API Gateway trả phản hồi đã xử lý về cho khách hàng.

---

### Lợi ích cho dự án này

Bằng cách sử dụng API Gateway và Lambda, chúng ta:

- Tránh quản lý máy chủ backend.
- Tự động mở rộng khi lưu lượng tăng đột biến.
- Triển khai endpoint mới nhanh chóng trong quá trình lab.
- Giữ chi phí thấp cho phát triển và thử nghiệm.

{{% notice tip %}}
Nếu bạn đang theo dõi các bài tập lab, bạn sẽ tích hợp các hàm Lambda của mình với API Gateway để xử lý toàn bộ logic backend — một **backend serverless** hoàn chỉnh.
{{% /notice %}}

[Đi tiếp và xem](7.1-indexFaceFunction/) cách triển khai RESTFUL API
