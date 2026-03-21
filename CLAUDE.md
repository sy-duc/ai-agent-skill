# AI Agent Skills

Bộ sưu tập các skill cá nhân dành cho AI agent.

## Cách kích hoạt skill

Khi người dùng yêu cầu một việc khớp với skill bên dưới → **tự động** đọc `skill.md` tương ứng và thực hiện theo hướng dẫn bên trong. Không cần người dùng chỉ định file.

### Danh sách skill

| Từ khoá kích hoạt | Skill | File |
|---|---|---|
| "báo cáo tuần", "report", "cresco" | Báo cáo tuần Cresco | `skills/cresco-weekly-report/skill.md` |

> Khi thêm skill mới, cập nhật bảng này.

## Cấu trúc thư mục

```
ai-agent-skills/
├── .github/prompts/         # Phiên bản Copilot (có frontmatter)
├── skills/                  # Phiên bản Claude Code
│   ├── registry.json        # Danh mục tất cả skill
│   ├── _template/           # Mẫu tạo skill mới
│   └── <skill-name>/
│       ├── skill.md          # Prompt/hướng dẫn chính
│       ├── template.md       # Template output (nếu có)
│       ├── config.json       # Metadata
│       └── output/           # Output tạm (gitignored)
├── shared/                  # Tài nguyên dùng chung
├── libs/                    # Thư viện bên ngoài
├── tests/                   # Kiểm thử
└── docs/                    # Tài liệu
```

## Quy ước

- Mỗi skill là thư mục self-contained trong `skills/`
- `skill.md` là entry point cho Claude Code
- `.github/prompts/<name>.prompt.md` là bản duplicate cho Copilot (có frontmatter)
- Khi sửa nội dung skill → sửa cả hai file
- Tên skill dùng kebab-case
- Đăng ký mọi skill mới vào `skills/registry.json` và bảng skill ở trên
