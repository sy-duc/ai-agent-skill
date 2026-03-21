# AI Agent Skills

Bộ sưu tập các kỹ năng (skills) cá nhân dành cho AI agent, được tổ chức theo dạng module để dễ dàng mở rộng và tái sử dụng.

Tương thích cả **Claude Code** và **GitHub Copilot**.

## Mục đích

Dự án này tập hợp các skill mà tôi xây dựng để phục vụ công việc hàng ngày với AI agent. Mỗi skill là một đơn vị độc lập, có thể sử dụng riêng lẻ hoặc kết hợp với nhau.

## Cấu trúc thư mục

```
ai-agent-skills/
├── .github/prompts/         # Phiên bản cho GitHub Copilot (có frontmatter)
├── skills/                  # Phiên bản cho Claude Code — nguồn chính
│   ├── registry.json        # Danh mục tổng hợp tất cả skill
│   ├── _template/           # Mẫu để tạo skill mới
│   └── <tên-skill>/         # Thư mục chứa skill
│       ├── skill.md          # Hướng dẫn / prompt chính
│       ├── template.md       # Template output (nếu có)
│       ├── config.json       # Thông tin: tên, phiên bản, thẻ, phụ thuộc
│       └── output/           # Output tạm — gitignored
├── shared/                  # Tài nguyên dùng chung giữa các skill
│   ├── prompts/             # Các đoạn prompt tái sử dụng
│   ├── schemas/             # Lược đồ dữ liệu chung
│   └── utils/               # Tiện ích dùng chung
├── libs/                    # Thư viện bên ngoài hoặc wrapper
├── tests/                   # Kiểm thử cho các skill
└── docs/                    # Tài liệu bổ sung
```

## Cách sử dụng skill

### Với Claude Code (Terminal)

Skill được **tự động kích hoạt** — chỉ cần mô tả yêu cầu bằng ngôn ngữ tự nhiên. Claude sẽ khớp từ khoá trong `CLAUDE.md`, tự đọc `skill.md` tương ứng và thực hiện.

```
tạo báo cáo tuần cresco
```

### Với GitHub Copilot (VS Code)

Mỗi skill có bản duplicate trong `.github/prompts/<tên-skill>.prompt.md` — có thêm YAML frontmatter để Copilot nhận diện.

1. Mở Copilot Chat trong VS Code (`Ctrl+Shift+I`)
2. Chuyển sang chế độ **Agent**
3. Gõ `#` → chọn prompt file tương ứng (ví dụ: `cresco-weekly-report`)
4. Copilot sẽ đọc hướng dẫn và tương tác với bạn

### Sự khác biệt giữa hai phiên bản

| | Claude Code (`skills/`) | Copilot (`.github/prompts/`) |
|---|---|---|
| Format | Markdown thuần | Markdown + YAML frontmatter |
| Gọi skill | Yêu cầu đọc `skill.md` | Gõ `#` chọn trong Copilot Chat |
| File hỗ trợ | `template.md`, `config.json`, `output/` | Không — tham chiếu về `skills/` |

Nội dung hướng dẫn **giống nhau**. Phiên bản Copilot chỉ thêm frontmatter ở đầu file. Các file hỗ trợ (`template.md`, `output/`) đều nằm trong `skills/` và được cả hai phiên bản tham chiếu.

> **Lưu ý:** Khi sửa nội dung skill, cần cập nhật cả hai file.

## Cách tạo skill mới

1. Sao chép thư mục `skills/_template/` thành `skills/<tên-skill>/`
2. Chỉnh sửa `skill.md` — viết hướng dẫn chi tiết
3. Cập nhật `config.json` — điền tên, mô tả, thẻ phân loại
4. Đăng ký skill vào `skills/registry.json`
5. Tạo bản Copilot:
   - Copy `skill.md` sang `.github/prompts/<tên-skill>.prompt.md`
   - Thêm frontmatter ở đầu file:
     ```yaml
     ---
     mode: agent
     description: Mô tả ngắn về skill
     ---
     ```

## Quy ước

- Tên skill dùng **kebab-case**: `code-review`, `git-commit-msg`
- Mỗi skill phải **tự đủ** (self-contained) trong thư mục của nó
- Logic dùng chung đặt trong `shared/`, không sao chép giữa các skill
- Mỗi skill cần có `skill.md` (bắt buộc) và `config.json` (bắt buộc)

## Phân loại skill

| Danh mục       | Mô tả                                      |
|----------------|---------------------------------------------|
| `coding`       | Sinh mã, tái cấu trúc, đánh giá code       |
| `research`     | Tìm kiếm, tổng hợp, phân tích thông tin    |
| `productivity` | Quản lý công việc, tự động hoá quy trình    |
| `writing`      | Viết nội dung, chỉnh sửa, dịch thuật       |
| `data`         | Xử lý, trực quan hoá, phân tích dữ liệu    |
| `devops`       | CI/CD, triển khai, hạ tầng                  |

## Danh sách skill hiện có

| Skill | Mô tả | Danh mục |
|-------|--------|----------|
| `cresco-weekly-report` | Tạo báo cáo công việc hàng tuần | `productivity` |

## Giấy phép

Dự án cá nhân — sử dụng tuỳ ý.
