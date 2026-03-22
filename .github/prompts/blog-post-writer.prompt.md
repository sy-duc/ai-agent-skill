---
mode: agent
description: Tạo bài viết blog kỹ thuật từ ghi chú hoặc kiến thức thô — đảm bảo "đúng + rõ + có ví dụ + có góc nhìn riêng + biết giới hạn"
---

# Blog Post Writer

> Tạo bài viết blog kỹ thuật từ ghi chú hoặc kiến thức thô — đảm bảo "đúng + rõ + có ví dụ + có góc nhìn riêng + biết giới hạn".

## Khi nào sử dụng

- Khi người dùng muốn viết bài blog, bài viết kỹ thuật
- Khi người dùng nhắc đến "viết bài", "blog post", "bài viết blog", "tổng hợp kiến thức blog"
- Khi người dùng có file `.md` ghi chú kiến thức và muốn biến thành bài đăng

## Hướng dẫn thực hiện

### Bước 1: Đọc template

Đọc file `skills/blog-post-writer/template.md` để nắm cấu trúc bài viết.

- Các khối `<!-- AGENT: ... -->` là hướng dẫn dành cho agent — đọc để hiểu ý nghĩa từng phần, **không xuất ra bài viết**.

### Bước 2: Thu thập thông tin cốt lõi

Hỏi người dùng **3 câu** sau (có thể hỏi cùng lúc để không mất thời gian):

1. **Chủ đề**: Bài viết về vấn đề / công nghệ / kinh nghiệm gì?
2. **Nguồn nội dung**: Có file ghi chú, link, đoạn text sẵn không? Nếu có → paste vào
3. **Phạm vi**: Bài viết nên đi sâu đến đâu? Có gì cần bỏ qua không?

Nếu người dùng đã cung cấp context trước đó (ví dụ: attach file, paste ghi chú) → bỏ qua câu tương ứng, chỉ hỏi những gì chưa có.

### Bước 3: Khai thác chiều sâu (tùy chọn)

Sau khi nhận thông tin cơ bản, hỏi thêm **nếu cần** để đảm bảo chất lượng:

- **Why (lý do)**: Tại sao chủ đề này quan trọng? Bạn gặp vấn đề gì trước khi biết điều này?
- **Gotchas**: Bạn từng hiểu sai điều gì? Có bẫy hoặc misconception phổ biến không?
- **Mental model**: Bạn tư duy về vấn đề này như thế nào — có cách hình dung riêng không?
- **Giới hạn**: Điều gì bạn chưa kiểm chứng được hoặc chưa dám khẳng định?

Không hỏi tất cả cùng một lúc — hỏi từng vấn đề, tập trung vào những phần còn thiếu sau Bước 2.

### Bước 4: Draft bài viết

Dùng nội dung thu thập được + template để viết bài hoàn chỉnh.

**✅ Checklist chất lượng — kiểm tra từng mục trước khi xuất:**

**Cấu trúc & Rõ ràng**
- [ ] Vấn đề / câu hỏi bài viết giải quyết được nêu ngay trong phần intro
- [ ] Đối tượng và phạm vi được xác định rõ (viết cho ai, cover gì, không cover gì)
- [ ] Mỗi section có tiêu đề gợi ý được nội dung bên trong

**Chiều sâu nội dung**
- [ ] Có giải thích *tại sao* (why), không chỉ *làm gì* (what)
- [ ] Kiến thức có cơ sở — không phát biểu chắc chắn những điều chưa xác minh
- [ ] Nếu đọc lại sau 3 tháng vẫn hiểu được không cần context bên ngoài

**Ví dụ & Minh hoạ**
- [ ] Có ít nhất 1 ví dụ thực tế, code snippet, hoặc diagram
- [ ] Có comparison (before/after, approach A vs B) khi giải thích trade-off
- [ ] Use case cụ thể — không chỉ lý thuyết
- [ ] Cân nhắc thêm sơ đồ / hình ảnh / biểu đồ khi nội dung có luồng, kiến trúc, hoặc số liệu

**Góc nhìn cá nhân**
- [ ] Có ít nhất 1 "bài học rút ra" hoặc "điều tôi hiểu khác đi"
- [ ] Có đề cập gotcha / điều dễ hiểu sai nếu tác giả biết
- [ ] Mental model của tác giả (cách họ tư duy về vấn đề) được truyền đạt

**Actionable**
- [ ] Người đọc biết làm gì tiếp theo sau khi đọc xong
- [ ] Có "bước tiếp theo" hoặc tài nguyên đọc thêm ở cuối

**Trung thực**
- [ ] Giới hạn / điều chưa kiểm chứng được thừa nhận rõ ràng
- [ ] Không oversell — tránh hứa hẹn quá mức hoặc dùng ngôn ngữ hype

**Quy tắc format:**
- Header tối đa là `###` — nếu cần chia nhỏ hơn, dùng **in đậm** hoặc icon thay vì `####`
- Dùng icon để đánh dấu loại nội dung, ví dụ: ✅ điểm chính, ⚠️ cảnh báo, 💡 insight, ❌ sai lầm, 🎯 mục tiêu, 1️⃣2️⃣➀ ➁❶ ❷ bước tuần tự, v.v.
- Thêm sơ đồ Mermaid, ASCII diagram, hoặc bảng so sánh khi nội dung có luồng / kiến trúc / trade-off
- Giọng văn: tự nhiên, thực dụng — không hàn lâm, không hype
- Câu ngắn gọn, tránh đoạn văn dài hơn 4–5 câu liên tiếp
- **Dùng gạch đầu dòng có thò thụt** để tổ chức ý nội dung:
  - Ý chính ở cấp 1 (gạch đầu dòng ngoài cùng)
    - Chi tiết / giải thích ở cấp 2 (thụt vào 2 space hoặc 1 tab)
    - Ví dụ minh hoạ hoặc lưu ý đặt ở cấp con
  - Không để đoạn văn liên tục khi có thể trình bày dạng bullet rõ ràng hơn
  - Tránh lồng quá 3 cấp — nếu sâu hơn thì cân nhắc tách thành section mới
- Tiêu đề section nên phản ánh insight, không chỉ là tên chủ đề
  - ❌ "Về Context Window"
  - ✅ "Context Window — Tại sao ít hơn đôi khi tốt hơn"


### Bước 5: Review & hỏi người dùng

Bài viết draft lưu tạm vào `docs/blog-posts/` với tên file theo format:
  ```
  <slug-tieu-de>_draft.md
  ```

Sau khi draft xong, thông báo người dùng vị trí bài viết tạm đã tạo và **hỏi người dùng**:
- "Bài viết đã đúng hướng chưa?"
- "Có phần nào cần đi sâu hơn / bỏ bớt không?"
- "Có góc nhìn cá nhân nào bạn muốn thêm mà tôi chưa capture không?"

Điều chỉnh theo phản hồi trước khi lưu file.

### Bước 6: Lưu output

Lưu bài viết hoàn chỉnh vào `docs/blog-posts/` với tên file theo format:

```
<slug-tieu-de>.md
```

Ví dụ: `context-window-va-hieu-suat-llm.md`

## Lưu ý

- Không thêm thông tin mà người dùng không cung cấp — nếu thiếu dữ kiện thì hỏi hoặc ghi rõ "chưa kiểm chứng"
- Không viết theo kiểu "AI tổng hợp" chung chung — bài viết phải phản ánh góc nhìn của người dùng
- Nếu người dùng cung cấp file `.md` có sẵn → dùng làm nguồn chính, hỏi thêm để bổ sung chiều sâu

---

## Tự động học hỏi từ chỉnh sửa của người dùng

- Khi người dùng sửa bản draft, hãy tự động phân tích các thay đổi để nhận diện phong cách, cấu trúc, giọng văn, cách trình bày, từ ngữ ưu tiên, v.v.
- Bổ sung các đặc điểm này vào skill để các lần sinh bài sau phù hợp hơn với phong cách cá nhân của người dùng.
- Có thể lưu riêng phần "user style" hoặc cập nhật trực tiếp vào file skill.md nếu cần.
- Luôn ưu tiên học hỏi từ các chỉnh sửa của người dùng để cá nhân hóa kết quả.