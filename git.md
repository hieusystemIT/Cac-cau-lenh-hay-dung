# Git Cheatsheet — Branch, Merge, Conflict

---

## Branch

```bash
# Tạo + switch ngay
git checkout -b gbizwebsite
git switch -c gbizwebsite          # cách mới, tương đương

# Switch sang branch đã có
git checkout gbizwebsite
git switch gbizwebsite

# ⚠️ checkout KHÔNG tự tạo branch — phải có -b mới tạo mới

# Xem danh sách branch
git branch                         # local
git branch -a                      # local + remote

# Xóa branch sau khi merge xong
git branch -d gbizwebsite
```

---

## Push lên Remote

```bash
# Push branch lên remote (lần đầu dùng -u để link)
git push -u origin gbizwebsite

# Những lần tiếp theo
git push

# Push branch bất kỳ
git push origin gbizwebsite        # push local "gbizwebsite" → remote "gbizwebsite"
                                   # remote chưa có thì tự tạo, có rồi thì update

# Xóa branch trên remote
git push origin --delete gbizwebsite

# Xem remote đang trỏ đến đâu
git remote -v
```

---

## Merge

```bash
# Merge feature vào main
git switch main
git merge --no-ff gbizwebsite

# Xem trước khi merge
git log main..gbizwebsite --oneline
```

---

## Fix Conflict

```bash
# 1. Xem file nào đang conflict
git status

# 2. Mở file, tìm và sửa tay các markers:
# <<<<<<< HEAD          ← nội dung branch hiện tại
# =======
# >>>>>>> gbizwebsite   ← nội dung branch merge vào
# → Xóa markers, giữ lại nội dung đúng

# 3. Đánh dấu đã resolve
git add <file>

# 4. Hoàn thành merge
git commit

# Hủy merge, làm lại từ đầu
git merge --abort
```

---

## Hay dùng kèm

```bash
git fetch --prune          # sync branch từ remote, xóa branch đã chết
git stash                  # cất thay đổi đang dở trước khi switch branch
git stash pop              # lấy lại thay đổi đã cất
```

---

## git checkout vs git switch

| | `git checkout` | `git switch` |
|---|---|---|
| Switch branch | ✅ | ✅ |
| Tạo branch mới | `checkout -b` | `switch -c` |
| Khôi phục file | ✅ | ❌ (dùng `git restore`) |
| Git version | Cũ | 2.23+ |

> `git checkout` vẫn dùng được bình thường, `git switch` rõ nghĩa hơn.

---

## Quick Reference

| Thao tác | Command |
|---|---|
| Tạo + switch branch | `git checkout -b <branch>` |
| Switch branch | `git checkout <branch>` |
| Push lần đầu | `git push -u origin <branch>` |
| Push tiếp theo | `git push` |
| Xóa branch local | `git branch -d <branch>` |
| Xóa branch remote | `git push origin --delete <branch>` |
| Merge vào main | `git switch main` → `git merge --no-ff <branch>` |
| Hủy merge dở | `git merge --abort` |
| Xem file conflict | `git status` |
| Hoàn thành merge | `git add <file>` → `git commit` |