# Checkin MKT192 WP — Release Channel

Kênh phát hành chính thức của plugin **Checkin MKT192 WP** (source code ở repo private).

- `manifest.json` — thông tin bản mới nhất; plugin trên các site khách tự đọc file này để báo update trong WP Admin.
- Gói cài đặt `.zip` đính kèm ở mục [Releases](../../releases).

## Quy trình phát hành bản mới

1. Build zip từ repo code — thư mục gốc trong zip phải là `checkin-mkt192-wp/`, loại trừ `.git`, `.claude`, `.mcp.json`:
   ```bash
   cd ~/Project
   zip -rq checkin-mkt192-wp-{VERSION}.zip checkin-mkt192-wp \
     -x "checkin-mkt192-wp/.git/*" "checkin-mkt192-wp/.git" \
        "checkin-mkt192-wp/.mcp.json" "checkin-mkt192-wp/.claude/*" "*/.DS_Store"
   ```
2. Tạo release và upload zip:
   ```bash
   gh release create v{VERSION} checkin-mkt192-wp-{VERSION}.zip \
     --repo monkeytech192/checkin-mkt192-wp-releases --title "v{VERSION}" --notes "..."
   ```
3. Cập nhật `manifest.json`: `version`, `package` (URL asset mới), `changelog`, `last_updated` → commit & push.
4. Site khách thấy update trong tối đa 6 giờ (cache manifest), hoặc ngay khi bấm **Check again** ở Dashboard → Updates.

## Lưu ý

- KHÔNG commit file zip vào git — zip chỉ upload làm release asset.
- Trường `package` trong manifest phải trỏ đúng URL asset của release tương ứng.
