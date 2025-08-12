---
title: "Thiết lập AWS CLI"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Cấu hình thông tin xác thực AWS

Trước khi triển khai bất kỳ tài nguyên nào, hãy đảm bảo AWS CLI của bạn được thiết lập với thông tin xác thực hợp lệ.  
{{% notice info %}}
Để xem hướng dẫn chi tiết, tham khảo [Bài lab 000011. Bắt đầu với AWS CLI](https://000011.awsstudygroup.com/).
{{% /notice %}}
Nếu bạn chưa thực hiện, hãy chạy:

```bash
aws configure
```

CLI sẽ yêu cầu ID khóa truy cập, Khóa truy cập bí mật, khu vực mặc định, và định dạng đầu ra.  
Ví dụ về thiết lập:  
Tạo tài khoản AWS: Nếu bạn chưa có tài khoản AWS, hãy đăng ký tại đây. Tài khoản AWS là bắt buộc để hoàn thành bài tập này.

Dưới đây là cách tạo người dùng IAM và thiết lập AWS CLI:

### Tạo nhóm IAM:

- Đăng nhập vào Bảng điều khiển quản lý AWS.
- Điều hướng đến dịch vụ IAM (Quản lý danh tính và truy cập).
- Tạo một nhóm IAM mới, đặt tên, và xác định các quyền cần thiết cho trường hợp sử dụng của bạn (trong trường hợp này, để thuận tiện, bạn nên chọn "AdministratorAccess" cho hồ sơ này, hoặc cấu hình sau trong hội thảo của tôi).
- Tạo người dùng IAM:

Vẫn trong dịch vụ IAM, tạo một người dùng IAM mới.

- Gán người dùng này vào nhóm IAM vừa tạo.
- Ghi lại ID khóa truy cập và Khóa truy cập bí mật để sử dụng sau này.
- Tạo khóa truy cập AWS:

Chọn người dùng IAM bạn đã tạo.

- Trong tab Thông tin xác thực bảo mật, tạo một cặp khóa truy cập mới.
- Lưu trữ an toàn ID khóa truy cập và Khóa truy cập bí mật—bạn sẽ cần chúng để xác thực với các dịch vụ AWS.

```bash
aws configure
AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
Default region name [None]: us-east-1
Default output format [None]: json
```

{{% notice warning %}}
Hãy nhớ đặt khu vực thành `us-east-1` hoặc các khu vực sau (vì Amplify và Rekognition Liveness chỉ khả dụng ở các khu vực này)  
| Tên khu vực | Mã khu vực |  
| ------------------------- | ---------------- |  
| **US East (Bắc Virginia)** | `us-east-1` |  
| **US West (Oregon)** | `us-west-2` |  
| **Châu Âu (Ireland)** | `eu-west-1` |  
| **Châu Á Thái Bình Dương (Tokyo)** | `ap-northeast-1` |  
| **Châu Á Thái Bình Dương (Mumbai)** | `ap-south-1` |

{{% /notice %}}

Nếu bạn muốn làm việc với một hồ sơ được đặt tên (có một trong các khu vực trên), hãy đặt nó làm hồ sơ hoạt động:

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
