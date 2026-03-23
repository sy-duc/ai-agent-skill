---
mode: agent
description: Tạo báo cáo công việc hàng tuần — ngắn gọn, súc tích, lịch sự
---

# Cresco Weekly Report

> Tạo báo cáo công việc hàng tuần — ngắn gọn, súc tích, lịch sự. Viết bằng tiếng Việt.

## Khi nào sử dụng

- Khi người dùng cần tạo báo cáo tuần
- Khi người dùng nhắc đến "báo cáo", "report", "cresco"

## Hướng dẫn thực hiện

### Bước 1: Đọc template & kiểm tra báo cáo cũ

Đọc file `skills/cresco-weekly-report/template.md` để nắm cấu trúc báo cáo hiện tại.

- Template có thể thay đổi theo thời gian — **luôn đọc lại mỗi lần chạy**
- Các khối `<!-- -->` trong template là **ghi chú dành cho agent** — đọc để hiểu ngữ cảnh của từng mục, nhưng KHÔNG xuất ra báo cáo
- Dựa vào ghi chú để biết cách chỉnh sửa câu văn cho phù hợp với từng mục

Kiểm tra thư mục `skills/cresco-weekly-report/output/` xem có báo cáo cũ không. Ghi nhớ nội dung báo cáo gần nhất (nếu có) để dùng ở Bước 3.

### Bước 2: Thu thập thông tin

Dựa vào các mục trong template, lần lượt hỏi người dùng. Quy tắc:

**Hỏi từng item trong mỗi mục:**

- Bắt đầu mục mới → hỏi item đầu tiên
- Sau mỗi câu trả lời → hỏi tiếp: "Còn gì nữa không? (bỏ qua để sang mục tiếp)"
- Người dùng bỏ qua → chuyển sang mục tiếp theo
- Lặp lại cho đến khi hết tất cả các mục trong template

**Subtask:**

- Khi hỏi mỗi task, gợi ý: "Nếu có nhiều subtask thì đánh số 1, 2, 3... cho mỗi subtask"
- Nếu task có subtask → hỏi thời gian hoàn thành ở **từng subtask** (không hỏi ở task cha)

**Trạng thái hoàn thành (Mục I — 対応済みタスク):**

- Sau khi người dùng nhập xong mỗi task/subtask → hỏi: "Xong chưa? Dự kiến bao giờ xong?"
- Trả lời xong rồi → ghi `（完了）` ở cuối dòng
- Trả lời ngày dự kiến → ghi `（dự kiến hoàn thành vào dd/mm）` ở cuối dòng
- Trả lời chưa biết / bỏ qua → không ghi gì thêm

**Thời gian dự kiến (Mục II — 来週の予定):**

- Sau khi người dùng nhập xong mỗi task/subtask → hỏi: "Dự kiến bao giờ xong?"
- Trả lời ngày dự kiến → ghi `（dự kiến hoàn thành vào dd/mm）` ở cuối dòng
- Trả lời chưa biết / bỏ qua → không ghi gì thêm

**Mục III — その他:**

- Nếu người dùng bỏ qua (không có vấn đề gì) → ghi mặc định: `・特に問題ありません。`

**Ví dụ luồng hỏi:**

```
Agent: 【Mục I — Công việc đã làm】
      Tuần trước bạn đã làm việc gì? (nếu có nhiều subtask thì đánh số 1,2,3...)
User: fix bug login
Agent: Xong chưa? Dự kiến bao giờ xong?
User: xong rồi
Agent: Còn việc nào nữa không? (bỏ qua để sang mục tiếp)
User: làm tính năng export CSV
      1. thiết kế DB
      2. code API
      3. code UI
Agent: Subtask 1 — thiết kế DB: xong chưa? Dự kiến bao giờ xong?
User: xong
Agent: Subtask 2 — code API: xong chưa? Dự kiến bao giờ xong?
User: dự kiến 25/3
Agent: Subtask 3 — code UI: xong chưa? Dự kiến bao giờ xong?
User: chưa biết
Agent: Còn việc nào nữa không? (bỏ qua để sang mục tiếp)
User: hết
Agent: 【Mục II — Kế hoạch tuần tới】
      Tuần tới bạn dự kiến làm gì? (nếu có nhiều subtask thì đánh số 1,2,3...)
...
```

**Lưu ý khi hỏi:**

- Câu hỏi ngắn gọn, rõ ràng
- Nếu người dùng trả lời gộp nhiều mục → ghi nhận và bỏ qua câu hỏi đã được trả lời

### Bước 3: Đối chiếu báo cáo cũ

Sau khi thu thập xong thông tin, kiểm tra thư mục `skills/cresco-weekly-report/output/`:

- **Không có báo cáo cũ** → bỏ qua bước này
- **Có báo cáo cùng ngày** → đây là bản sửa, sẽ ghi đè ở bước 5
- **Có báo cáo ngày trước đó** → so sánh:
  - Tìm các task/subtask trong báo cáo cũ **chưa hoàn thành** (không có `完了`)
  - Nếu task đó **không được đề cập** trong báo cáo mới → hỏi người dùng:
    "Báo cáo trước có task [tên task] chưa xong. Tình trạng hiện tại thế nào?"
  - Dựa vào câu trả lời → thêm vào báo cáo mới hoặc bỏ qua

### Bước 4: Chỉnh sửa câu văn

Người dùng có thể trả lời bản thô, rời rạc, viết tắt. Nhiệm vụ của bạn:

- Chỉnh thành câu văn hoàn chỉnh, mạch lạc
- Giữ ngắn gọn, súc tích — không thêm thắt thông tin không có
- Giọng văn lịch sự, chuyên nghiệp (báo cáo gửi khách hàng)
- Dùng bullet point, tránh đoạn văn dài
- KHÔNG thêm thông tin mà người dùng không cung cấp
- Tham khảo ghi chú trong template để chỉnh văn phong phù hợp từng mục

### Bước 5: Xuất báo cáo & lưu output

- Xuất báo cáo theo đúng cấu trúc template (bỏ toàn bộ comment)
- Hiển thị trực tiếp dạng text cho người dùng review
- Hỏi người dùng muốn chỉnh sửa gì không
- Nếu có chỉnh sửa → sửa và hiển thị lại
- Khi người dùng xác nhận → lưu báo cáo vào `skills/cresco-weekly-report/output/report-YYYY-MM-DD.md`
  - Nếu đã có file cùng ngày → ghi đè

## Lưu ý

- Báo cáo tạo ra luôn viết bằng tiếng Việt có dấu dù cho template đang dùng ngôn ngữ khác
- Người nhận là khách hàng → giọng văn cần **chuyên nghiệp, lịch sự**
- Ưu tiên **ngắn gọn** hơn là chi tiết dài dòng
