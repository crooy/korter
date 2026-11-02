# Cách cài đặt

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Cài đặt

```bash
agy plugin install https://github.com/ayghri/mand
```

### Xác minh

```bash
agy plugin list
```

### Cập nhật

```bash
agy plugin uninstall mand
agy plugin install https://github.com/ayghri/mand
```

### Gỡ cài đặt

```bash
agy plugin uninstall mand
```

Hoặc giữ nguyên cài đặt và tắt bằng `agy plugin disable mand`.

### Luôn bật (không bắt buộc)

Thêm vào `~/.gemini/GEMINI.md`:

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Cài đặt

```bash
claude plugin marketplace add ayghri/mand
claude plugin install mand@mand
```

Gõ `/mand`.

### Xác minh

```bash
claude plugin list
```

### Cập nhật

```bash
claude plugin marketplace update mand
claude plugin update mand@mand
```

### Gỡ cài đặt

```bash
claude plugin uninstall mand
claude plugin marketplace remove mand
```

Hoặc giữ nguyên cài đặt và tắt bằng `claude plugin disable mand`.

### Luôn bật (không bắt buộc)

Hook `SessionStart` tải toàn bộ bộ quy tắc khi bắt đầu mỗi phiên, không cần `/mand`:

```bash
touch ~/.claude/.mand-always
```

Nếu bạn dùng thư mục cấu hình Claude tùy chỉnh, hãy tạo tệp cờ ở đó thay vào đó:

```bash
touch "$CLAUDE_CONFIG_DIR/.mand-always"
```

Để trở lại chế độ bật khi cần:

```bash
rm ~/.claude/.mand-always
```

Hook chỉ chạy khi tệp cờ tồn tại, vì vậy chỉ cài plugin sẽ không tự thay đổi gì. "stop mand" vẫn tắt chế độ này cho phiên hiện tại.

</details>


<details>
<summary><strong>Codex</strong></summary>

### Cài đặt

```bash
codex plugin marketplace add ayghri/mand --ref main
codex plugin add mand@mand
```

Gọi skill một cách rõ ràng bằng cách gõ `$mand`. Codex sẽ không tự động kích hoạt skill.

### Xác minh

```bash
codex plugin list
```

### Cập nhật

```bash
codex plugin marketplace upgrade mand
codex plugin remove mand
codex plugin add mand@mand
```

### Gỡ cài đặt

```bash
codex plugin remove mand
codex plugin marketplace remove mand
```

### Luôn bật (không bắt buộc)

Thêm vào `~/.codex/AGENTS.md`:

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI không có chợ plugin nên có hai cách tích hợp sẵn: **lệnh tùy chỉnh** (chỉ bật khi gọi) hoặc **extension** (luôn bật sau khi cài). Cách dùng lệnh phù hợp với hành vi mặc định của skill; hãy chọn cách này trừ khi bạn muốn áp dụng quy tắc cho mọi phiên.

### Cài đặt (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/ayghri/mand/main/skills/mand/agents/gemini.toml \
  -o ~/.gemini/commands/mand.toml
```

Bắt đầu phiên mới và gõ `/mand`. Skill sẽ bật trong suốt phiên đó.

### Cài đặt (extension, always-on)

```bash
gemini extensions install https://github.com/ayghri/mand
```

Extension tải `GEMINI.md`, tệp nhập toàn bộ skill, nên quy tắc được áp dụng từ tin nhắn đầu tiên. Máy phải cài `git`.

### Xác minh

```bash
gemini extensions list          # cách dùng extension
ls ~/.gemini/commands           # command route: mand.toml present
```

Hoặc gõ `/` trong một phiên và xác nhận `mand` có trong danh sách.

### Cập nhật

```bash
gemini extensions update mand    # cách dùng extension
# cách dùng lệnh: chạy lại curl ở trên
```

### Gỡ cài đặt

```bash
gemini extensions uninstall mand    # cách dùng extension
rm ~/.gemini/commands/mand.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

Copilot đọc Agent Skills trực tiếp: cùng một `SKILL.md`, không cần chuyển đổi. Trong dự án, Copilot quét `.github/skills/`, `.claude/skills/`, `.agents/skills/`; trên toàn hệ thống, nó quét `~/.copilot/skills/`, `~/.claude/skills/`, `~/.agents/skills/`.

### Cài đặt

```bash
npx skills add ayghri/mand -a github-copilot        # dự án này
npx skills add ayghri/mand -a github-copilot -g     # mọi dự án
```

Nếu không dùng CLI, hãy sao chép thư mục skill vào bất kỳ thư mục nào Copilot quét:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.copilot/skills
cp -R mand/skills/mand ~/.copilot/skills/
```

### Xác minh

Gõ `/` trong ô chat và xác nhận `mand` xuất hiện. Hoặc:

```bash
npx skills list
npx skills ls -g    # nếu đã cài toàn cục
```

### Cập nhật

```bash
npx skills update mand
```

Hoặc sao chép lại thư mục sau `git pull`.

### Gỡ cài đặt

```bash
npx skills remove mand
```

Hoặc xóa thư mục `mand` khỏi thư mục skills nơi nó được cài.

### Lưu ý về kích hoạt

Copilot tuân theo `disable-model-invocation`: không có gì được áp dụng cho đến khi bạn gọi skill, giống Claude Code (đã kiểm thử trong [#60](https://github.com/ayghri/mand/pull/60)).

### Luôn bật (không bắt buộc)

Thêm khối dưới đây vào `.github/copilot-instructions.md` của dự án (Copilot đọc nó trong mọi cuộc chat):

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>

<details>
<summary><strong>Hermes</strong></summary>

### Cài đặt

```bash
hermes skills install ayghri/mand/skills/mand
```

Gõ `/mand`. The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

Muốn xem trước? Thêm repo này làm nguồn skill (một "tap"), rồi tìm kiếm và cài đặt:

```bash
hermes skills tap add ayghri/mand
hermes skills search mand
hermes skills install ayghri/mand/skills/mand
```

### Xác minh

```bash
hermes skills list
```

### Cập nhật

```bash
hermes skills update mand
```

### Gỡ cài đặt

```bash
hermes skills uninstall mand
```

Hoặc xóa cả tap bằng `hermes skills tap remove ayghri/mand`.

### Luôn bật (không bắt buộc)

Thêm vào `AGENTS.md` trong thư mục làm việc (Hermes tải theo từng thư mục), hoặc vào `SOUL.md` của persona để dùng cho mọi phiên:

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Cài đặt

Hãy bắt đầu một phiên Kimi Code, rồi:

1. Chạy `/plugins`.
2. Chọn **Custom**.
3. Dán `https://github.com/ayghri/mand` rồi nhấn Enter.
4. Chọn **Trust and install**.

Dùng lệnh slash `/skill:mand` để gọi skill một cách rõ ràng.

### Cập nhật

Trong phiên Kimi Code, chạy `/plugins`, đưa con trỏ đến **mand**, rồi nhấn `R`.

### Gỡ cài đặt

Trong phiên Kimi Code, chạy `/plugins`, đưa con trỏ đến **mand**, rồi nhấn `D`.

</details>


<details>
<summary><strong>OpenCode</strong></summary>

Plugin hỗ trợ OpenCode V1 **từ 1.18.29** và V2. Plugin đăng ký skill, lệnh `/mand` và chế độ luôn bật tùy chọn. V1 cũ hơn cần nâng cấp hoặc dùng plugin từ bản phát hành skill trước đó.

### Cài đặt

Để dùng trong mọi dự án:

```bash
git clone https://github.com/ayghri/mand ~/.config/opencode/vendor/mand
mkdir -p ~/.config/opencode/plugins
cat > ~/.config/opencode/plugins/mand.js <<'EOF'
export { default } from '../vendor/mand/.opencode/plugins/mand.mjs';
EOF
```

Với cài đặt V1 hiện có, giữ mục `plugin` trong `opencode.json`. Nếu chuyển sang tệp nạp ở trên, hãy xóa mục đó.

Mở phiên mới và nhập `/mand`. Các quy tắc duy trì đến khi bạn nói `stop mand` hoặc `normal mode`.

#### Chỉ skill và lệnh (không có chế độ luôn bật)

Hoặc sao chép skill và lệnh từ kho mã vào các thư mục toàn cục của OpenCode:

```bash
mkdir -p ~/.config/opencode/skills/mand ~/.config/opencode/commands
cp skills/mand/SKILL.md ~/.config/opencode/skills/mand/SKILL.md
cp .opencode/command/mand.md ~/.config/opencode/commands/mand.md
```

### Kiểm tra

Khởi động OpenCode, nhập `/` và xác nhận `mand` có trong danh sách lệnh.

### Cập nhật

```bash
git -C ~/.config/opencode/vendor/mand pull
```

Với cách cài bằng sao chép, cập nhật kho mã rồi sao chép lại hai tệp.

### Gỡ cài đặt

Xóa `~/.config/opencode/plugins/mand.js`. Với cách cài bằng sao chép, xóa `~/.config/opencode/skills/mand/` và `~/.config/opencode/commands/mand.md`. Với cài đặt V1 dùng cấu hình hiện có, xóa mục `plugin` tương ứng.

### Luôn bật (không bắt buộc)

Cần plugin. Khi tạo tệp cờ, toàn bộ quy tắc được thêm vào lời nhắc hệ thống ở mỗi lượt:

```bash
touch ~/.config/opencode/.mand-always
```

`stop mand` hoặc `normal mode` yêu cầu agent trở lại cách trả lời mặc định trong phiên hiện tại. Xóa tệp cờ để ngừng tự động thêm quy tắc:

```bash
rm ~/.config/opencode/.mand-always
```

Nếu có đặt `XDG_CONFIG_HOME`, thay `~/.config` trong các đường dẫn này bằng thư mục đó.

</details>

<details>
<summary><strong>Pi</strong></summary>

Pi triển khai chuẩn Agent Skills nên tải trực tiếp cùng một `SKILL.md`, không cần chuyển đổi. Cách gọi của Pi khác các công cụ khác: skill được gọi bằng `/skill:<name>`.

### Cài đặt

```bash
npx skills add ayghri/mand -a pi -y
```

Muốn dùng hệ thống tệp? Pi tìm skill trong `~/.pi/agent/skills/` và `~/.agents/skills/` (toàn cục), cùng `.pi/skills/` và `.agents/skills/` (dự án):

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.pi/agent/skills
cp -R mand/skills/mand ~/.pi/agent/skills/
```

Bật lệnh gạch chéo cho skill trong `settings.json` của Pi:

```json
{ "enableSkillCommands": true }
```

Bắt đầu phiên mới và gõ `/skill:mand`.

### Xác minh

```bash
npx skills list
```

Hoặc gõ `/skill:` trong một phiên và xác nhận `mand` có trong danh sách.

### Cập nhật

```bash
npx skills update mand
```

Hoặc sao chép lại thư mục sau `git pull`.

### Gỡ cài đặt

```bash
npx skills remove mand
```

Hoặc xóa `~/.pi/agent/skills/mand`.

### Luôn bật (không bắt buộc)

Thêm vào `AGENTS.md` của dự án:

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### Cài đặt

```bash
qwen extensions install ayghri/mand
```

Qwen Code hỗ trợ dạng viết tắt GitHub và cài kho lưu trữ này dưới dạng extension gốc. Extension sẽ phát hiện skill trong `skills/`.

Gõ `/mand` để gọi skill một cách rõ ràng. Chỉ cài extension sẽ không thay đổi đầu ra cho đến khi skill được gọi.

### Xác minh

```bash
qwen extensions list
```

Sau đó, bắt đầu một phiên Qwen Code mới và chạy:

```text
/skills
```

Xác nhận `mand` xuất hiện trong danh sách.

### Cập nhật

```bash
qwen extensions update mand
```

### Gỡ cài đặt

```bash
qwen extensions uninstall mand
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Agent của Zed đọc Agent Skills trực tiếp: cùng một `SKILL.md`, không cần chuyển đổi. ("Rules" cũ của Zed đã được thay bằng Skills cùng hướng dẫn trong `AGENTS.md`.)

### Cài đặt

Trong Agent Panel, mở trình quản lý Skills, chọn **Create skill from URL** (cũng có trong bảng lệnh dưới tên `agent: create skill from url`), rồi dán:

```
https://github.com/ayghri/mand/blob/main/skills/mand/SKILL.md
```

Lưu ở phạm vi **User** cho mọi dự án hoặc **Project** cho một dự án. Sau đó gõ `/mand` trong Agent Panel.

Muốn dùng hệ thống tệp? Clone repo và đặt thư mục skill vào thư mục skills của người dùng:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.agents/skills
cp -R mand/skills/mand ~/.agents/skills/
```

### Xác minh

Mở trình quản lý Skills trong Agent Panel và xác nhận `mand` có trong danh sách. Hoặc gõ `/` và xác nhận nó xuất hiện.

### Cập nhật

Nhập lại từ cùng URL (ghi đè), hoặc sao chép lại thư mục sau `git pull`.

### Gỡ cài đặt

Xóa `mand` khỏi trình quản lý Skills, hoặc xóa `~/.agents/skills/mand`.

### Luôn bật (không bắt buộc)

Thêm vào `~/.config/zed/AGENTS.md` cá nhân:

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```

</details>

<details>
<summary><strong>Cursor, Amp và mọi môi trường agent-skills khác</strong></summary>

Hoạt động với mọi môi trường đọc Agent Skills. Thay `-a <agent>` bằng agent của bạn.

### Cài đặt

```bash
npx skills add ayghri/mand                  # this workspace
npx skills add ayghri/mand -g               # mọi dự án
npx skills add ayghri/mand -a cursor -y     # one agent only
npx skills add ayghri/mand -a opencode -y
```

Mở cuộc chat agent mới và gõ `/mand`.

Nếu không dùng CLI, sao chép thư mục skill vào đường dẫn mà agent quét:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.cursor/skills     # Cursor. Dùng .agents/skills cho OpenCode hoặc đường dẫn riêng của agent
cp -R mand/skills/mand ~/.cursor/skills/
```

### Xác minh

```bash
npx skills list
npx skills ls -g    # nếu đã cài toàn cục
```

### Cập nhật

```bash
npx skills update mand
npx skills update -g    # nếu đã cài toàn cục
```

### Gỡ cài đặt

```bash
npx skills remove mand
npx skills remove mand -g    # nếu đã cài toàn cục
```

### Luôn bật (không bắt buộc)

Dán nội dung này vào tệp quy tắc lâu dài của agent. Cursor: **Settings → Rules → User Rules**, hoặc quy tắc dự án trong `.cursor/rules/` với `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Phong cách đầu ra

Trả lời ngắn gọn và đi thẳng vào hành động. Định dạng mọi phản hồi để có thể thực hiện ngay:

1. Bắt đầu bằng câu trả lời hoặc hành động tiếp theo: ưu tiên lệnh, đường dẫn hoặc đoạn mã.
2. Đánh số công việc nhiều bước; mỗi bước chỉ có một hành động rõ ràng.
3. Kết thúc bằng một hành động tiếp theo có thể làm trong chưa đến hai phút.
4. Hoàn tất vấn đề hiện tại trước khi nêu vấn đề mới.
5. Nhắc lại tiến độ ở mỗi lượt ("đã xong bước 3/5").
6. Ước tính thời gian bằng đơn vị cụ thể, không nói "một chút".
7. Sau khi thay đổi, hãy cho biết điều gì hiện đã hoạt động.
8. Với lỗi, nêu vị trí, nguyên nhân và cách sửa một cách khách quan.
9. Giới hạn danh sách ở 5 mục.
10. Không mở đầu, không tóm tắt lại, không lời kết.

Ngoại lệ: giải thích đầy đủ khi được yêu cầu. Xác nhận trước thao tác phá hủy dữ liệu. Sau ba lần sửa thất bại, dừng lại và nêu giả định đáng ngờ. Nếu yêu cầu mơ hồ, hãy hỏi một câu ngắn.
```
</details>


## Cơ chế kích hoạt

1. **Đã cài nhưng chưa gọi.** Trong Claude Code, Qwen Code và Codex, không có gì xảy ra cho đến khi bạn gọi skill một cách rõ ràng. Claude Code và Qwen Code tuân theo `disable-model-invocation: true` trong `SKILL.md`; Codex tuân theo `policy.allow_implicit_invocation: false` trong `agents/openai.yaml`. Các môi trường khác có thể tải mô tả của từng skill khi khởi động và tự kích hoạt.
2. **Bạn gọi skill một cách rõ ràng.** Gõ `/mand` trong Claude Code hoặc Qwen Code, hoặc `$mand` trong Codex. Quy tắc bật trong phiên đó. "stop mand" hoặc "normal mode" sẽ tắt chúng.
3. **Bạn tạo `~/.claude/.mand-always`** (Claude Code). Hook `SessionStart` tải toàn bộ quy tắc từ tin nhắn đầu tiên trong mọi phiên.
4. **Bạn thêm đoạn luôn bật ở trên** (các môi trường khác). Điều này giữ quy tắc cốt lõi trong ngữ cảnh lâu dài của agent.

Trong Claude Code, Qwen Code và Codex không có trạng thái trung gian: nếu bạn chưa bật thì nó đang tắt.

## Khắc phục sự cố

**`/mand` không có trong tự động hoàn thành.** Khởi động lại agent. Chỉ mục plugin được đọc khi khởi động.

**Cờ luôn bật không có tác dụng.** Cập nhật plugin (`claude plugin marketplace update mand`, sau đó `claude plugin update mand@mand`) và khởi động lại. Hook được đọc khi khởi động, và cờ cần phiên bản plugin có `hooks/hooks.json`.

**`claude plugin marketplace add` thất bại.** Dùng dạng `owner/repo`. Đường dẫn cục bộ phải trỏ đến thư mục gốc repo, không phải `.claude-plugin/`.

**Đã cài nhưng phản hồi vẫn có lời mở đầu.** Mở phiên mới. Nếu vẫn lệch, hãy làm chặt hơn cách diễn đạt trong `skills/mand/SKILL.md`.

**Muốn quy tắc khác.** Fork repo, sửa `skills/mand/SKILL.md`, rồi chuyển sang bản của bạn:

```bash
claude plugin uninstall mand            # gỡ bản upstream trước:
claude plugin marketplace remove mand   # fork và upstream dùng cùng tên
claude plugin marketplace add <your-username>/mand
claude plugin install mand@mand
```

Khởi động lại rồi gọi `/mand` lần nữa.

**Thiếu skill sau `npx skills add`.** Mở cuộc chat agent mới. Skill được lập chỉ mục khi bắt đầu phiên. Xác nhận thư mục nằm ở nơi agent quét (`~/.cursor/skills/` cho Cursor, `.agents/skills/` cho OpenCode) và `name` trong frontmatter khớp tên thư mục.
