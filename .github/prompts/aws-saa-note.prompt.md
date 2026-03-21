---
mode: agent
description: Tóm tắt kiến thức từ giải thích đáp án khi luyện đề AWS SAA và bổ sung vào Learning Map
---

# AWS Practice Note

> Tóm tắt kiến thức từ giải thích đáp án khi luyện đề AWS SAA và bổ sung vào Learning Map.

## Khi nào sử dụng

- Khi người dùng paste đoạn text giải thích đáp án có chứa `Tóm tắt đề`, `Đáp án đúng`, `Tips and tricks`
- Khi người dùng nhắc đến "luyện đề AWS", "saa note", "thêm vào learning map"

## Hướng dẫn thực hiện

### Bước 1: Tìm vị trí chèn trong file

Dùng grep search pattern `\| \*\*.*\*\* \|` trong file `docs/aws/aws-saa-note.md` để lấy **tất cả các dòng category header** và line number tương ứng.

Từ kết quả đó, xác định:
- Line number của category cần chèn (ví dụ: `| **🔒 Security** |`)
- Line number của category **tiếp theo** ngay sau đó

Đọc đoạn từ dòng category header đến dòng header tiếp theo → **row cuối cùng trong đoạn đó chính là điểm chèn**.

### Bước 2: Phân tích input

Từ đoạn text người dùng cung cấp, trích xuất:

1. **Keyword** (từ `Tóm tắt đề`): 1 cụm từ ngắn hoặc câu keyword phản ánh tình huống/yêu cầu trong đề — tương tự các keyword đang có trong cột `Tình huống / Keyword trong đề`

2. **Service / Giải pháp chính** (từ `Đáp án đúng`): Tên dịch vụ AWS hoặc giải pháp cụ thể — viết in đậm như các dòng hiện có

3. **Ghi chú** (từ `Tips and tricks`): Tóm gọn lý do tại sao service này là lựa chọn đúng — 1–2 câu, tiếng Việt, phong cách giải thích như các row hiện có

4. **Category**: Xác định category phù hợp dựa trên service:

| Category | Các service điển hình |
|---|---|
| 🔒 Security | IAM, KMS, WAF, GuardDuty, Shield, Cognito, Secrets Manager, Inspector, Macie, ACM, Security Hub, Control Tower, SCPs, Session Manager, S3 Object Lock |
| 🌐 Networking | VPC, CloudFront, Route53, ALB, NLB, Global Accelerator, Direct Connect, Transit Gateway, PrivateLink, VPN, Gateway Endpoint |
| 💻 Compute | EC2, Lambda, ECS, EKS, Fargate, Auto Scaling, Step Functions, AWS Batch |
| 🚚 Migration | Application Migration Service, Snowball, Application Discovery Service, DMS |
| 🗄️ Storage | S3, EBS, EFS, FSx, Storage Gateway, AWS Backup, S3 Glacier |
| 🗃️ Database | RDS, Aurora, DynamoDB, ElastiCache, Neptune, Redshift, RDS Proxy |
| 💬 Messaging | SQS, SNS, EventBridge, Kinesis (streaming/messaging), SES |
| 📊 Analytics / AI | Athena, Glue, QuickSight, OpenSearch, Kinesis Data Analytics, Rekognition, Comprehend, CloudWatch |
| 💰 Cost Optimization | Cost Explorer, Savings Plans, Reserved Instances, Spot Instances, Compute Optimizer, Cost Allocation Tags |
| ⚙️ Management / Governance | CloudFormation, Systems Manager, Config, CloudTrail, Organizations, Service Catalog |

Nếu thuộc 1 category mới chưa có trong bảng → tạo category mới nếu cần thiết (thêm vào vị trí cuối cùng của bảng `Learning Map AWS SAA`).

### Bước 3: Kiểm tra trùng lặp

Trước khi chèn, search trong file **tên service vừa xác định** để kiểm tra:

- **Nếu trùng** (keyword và service tương tự): Dừng lại, không thêm. Báo người dùng "Kiến thức này đã có trong Learning Map."
- **Nếu service đã có nhưng keyword khác** (bổ sung thêm góc độ mới): Chèn row mới **ngay bên dưới dòng cuối cùng có service đó**, thay vì cuối block category.
- **Nếu service chưa có**: Chèn vào cuối block category như bình thường.

### Bước 4: Thêm row vào bảng

Chèn row mới theo kết quả bước 3.

**Format row cần thêm:**
```
| | <Keyword> | **<Service>** | <Ghi chú> |
```

**Quy tắc chèn:**
- Tìm block category tương ứng (ví dụ: `| **🔒 Security** | | | |`)
- Chèn row mới ở **cuối block category đó**, **trước khi bắt đầu category tiếp theo** (hoặc ngay sau service đã có nếu bổ sung)
- Nếu có nhiều service cho cùng 1 keyword, mỗi service một row, dòng thứ 2 trở đi để trống cột Category và Keyword:
  ```
  | | <Keyword> | **<Service 1>** | <Ghi chú 1> |
  |         |           | **<Service 2>** | <Ghi chú 2> |
  ```
- **Không** thêm dòng trống thừa giữa các row

### Bước 5: Xác nhận

Sau khi thêm vào file, trả lời người dùng theo format dễ đọc sau (không dùng table):

```
✅ Đã thêm vào [Category]

- Keyword  : <Keyword>
- Service  : <Service>
- Ghi chú  : <Ghi chú>
```

## Ví dụ

### Input mẫu

```
Tóm tắt đề:
Cần lưu log của tất cả API calls đến AWS services để phục vụ audit và compliance.

Đáp án đúng:
AWS CloudTrail

Tips and tricks:
CloudTrail ghi lại toàn bộ lịch sử API calls (ai gọi, gọi gì, khi nào, từ đâu) — đây là service duy nhất chuyên cho audit trail và compliance logging.
```

### Output mẫu

```
✅ Đã thêm vào ⚙️ Management / Governance

- Keyword  : Audit trail + API calls logging
- Service  : AWS CloudTrail
- Ghi chú  : CloudTrail ghi lại toàn bộ lịch sử API calls (ai gọi, gọi gì, khi nào, từ đâu) — service duy nhất chuyên cho audit trail và compliance logging
```
