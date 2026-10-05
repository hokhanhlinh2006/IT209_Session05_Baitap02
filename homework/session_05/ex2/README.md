# Bài 2: Tái cấu trúc lịch sử commit bằng Interactive Rebase

## Các bước thực hiện

### 1. Chuẩn bị (Tạo 4 commit ban đầu)
Tạo lần lượt 4 commit với nội dung như sau:
- Commit 1: `feat: khoi tao module auth`
- Commit 2: `fix typo`
- Commit 3: `adds utility functions`
- Commit 4: `add temp file for debug`

### 2. Chạy lệnh Interactive Rebase
Sử dụng lệnh sau để lùi về 4 commit trước:
```bash
git rebase -i HEAD~4
```

### 3. Cấu hình giao diện soạn thảo (Rebase Todo)
Trong trình soạn thảo được mở lên, tiến hành sửa lệnh thực thi cho các commit (gộp 3 commit đầu và bỏ qua commit cuối).
Nội dung file todo được chỉnh sửa thành:

```text
pick 8634c0a feat: khoi tao module auth
squash 84faf98 fix typo
squash d918737 adds utility functions
drop e1cad04 add temp file for debug

# Rebase 921a3f5..e1cad04 onto 921a3f5 (4 commands)
#
# Commands:
# p, pick <commit> = use commit
# ...
```

### 4. Đổi tên thông điệp commit (Reword/Squash message)
Sau khi lưu file todo và đóng lại, Git tự động thực hiện việc squash và yêu cầu soạn thảo lại thông điệp chung cho các commit được gộp. 
Tôi đã xóa các thông điệp cũ và đổi thành:

```text
feat: hoan thien module authentication
```

### 5. Kết quả
Kiểm tra lại lịch sử commit bằng lệnh `git log --oneline`, lịch sử giờ đây rất gọn gàng:

```text
$ git log --oneline
4ede9c4 (HEAD -> master) feat: hoan thien module authentication
921a3f5 Initial commit
```

Như vậy, tính năng đã được gom vào 1 commit duy nhất sạch sẽ và file rác `temp.txt` ở commit thứ 4 cũng đã bị loại bỏ hoàn toàn.
