# 01: Làm việc BRANCH

## 1 `branch` là gì?

`branch` là những phân nhánh ghi lại luồng thay đổi của lịch sử, các hoạt động trên mỗi branch sẽ không ảnh hưởng lên các branch khác nên có thể tiến hành nhiều thay đổi đồng thời trên một repository, giúp giải quyết được nhiều nhiệm vụ cùng lúc.

## 2 `branch` master

Khi bạn tạo một repository thì Git sẽ thiết lập branch mặc định là master, nghĩa là nó sẽ tự tạo một branch master và mọi hoạt động của ban lúc này đều nằm trên branch master. Chúng ta cũng có thể xem đây là branch mặc định đóng vai trò cập nhật dữ liệu và đồng bộ với remote repository.

## 3 Tạo branch

Branch có thể tạo bằng lệnh branch.
Ở đây, hãy thử tạo branch với tên issue1.

```
$ git branch issue1
```

Khi thực hiện lệnh branch mà không chỉ định tham số, thì có thể hiển thị danh sách các branch. Ở đầu có dấu * là branch hiện tại.

```
$ git branch
  issue1
* master
```

## 4 Chuyển đổi branch

Để thêm commit vào branch issue1 đã tạo mới, thì cần checkout branch issue1.

Checkout branch sẽ thực hiện bằng lệnh checkout.
Checkout branch issue1.

```
$ git checkout issue1
Switched to branch 'issue1'
```

Note: Nếu chỉ định lựa chọn -b trong lệnh checkout rồi thực hiện, thì có thể tóm gọn thực hiện cả tạo branch và checkout.

```
$ git checkout -b <branch>
```

## 5 Merge branches

Merge branch sẽ được thực hiện bằng lệnh merge.

```
$ git merge <commit>
```

Bằng lệnh này, branch đã chỉ định sẽ được đưa vào branch đang chỉ định của HEAD.

Để đưa issue1 vào branch master, thì trước hết sẽ di chuyển đến branch master, sau đó merge commit issue1 vào master.

```
$ git checkout master
Switched to branch 'master'

$ git merge issue1
Updating 1257027..b2b23c4
Fast-forward
 myfile.txt |    1 +
 1 files changed, 1 insertions(+), 0 deletions(-)
```

## 6 Xóa branch

Để xóa branch thì hãy chỉ định lựa chọn -d trong lệnh branch rồi thực hiện.

```
$ git branch -d issue1
Deleted branch issue1 (was b2b23c4).
```

Như thế, branch issue1 đã được xóa. Bằng lệnh branch hãy kiểm tra thử xem branch đã được xóa chưa.

```
$ git branch
* master
```

## 7 Giải quyết xung đột bằng merge 

Bây giờ, hãy tích hợp thay đổi tại branch issue2 và thay đổi tại branch issue3 vào master.

Trước tiên, sau khi đã checkout trên branch master, thực hiện merge branch issue2.

```
$ git checkout master
Switched to branch 'master'
$ git merge issue2
Updating b2b23c4..8f7aa27
Fast-forward
 myfile.txt |    2 ++
 1 files changed, 2 insertions(+), 0 deletions(-)
 ```

Tiếp theo, thực hiện merge branch issue3.
```
$ git merge issue3
Auto-merging myfile.txt
CONFLICT (content): Merge conflict in myfile.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Ở những chổ có xung đột thì Git đang chèn vào phần khác biệt như dưới:
```
<<<<<<< HEAD
commit: Lưu lại trạng thái của index
=======
pull: Lấy nội dung của remote repository
>>>>>>> issue3
```

Chúng ta có thể resolve conflict bằng cách **Accept Current Change/Accept Incoming Change/Accept  Both Changes**

Sau khi chỉnh sửa nơi xung đột xong hãy commit lại.

```
$ git add myfile.txt
$ git commit -m "Thực hiện merge branch issue3"
# On branch master
nothing to commit (working directory clean)
```
## 8 Merge bằng rebase

Khi merge branch issue3, nếu rebase nhánh issue3 trước thì cũng có thể hợp nhất lịch sử.

Tạm thời, hãy xóa merge trước đó.

```
$ git reset --hard HEAD~
```

Sau khi checkout với branch issue3, hãy thực hiện rebase đối với master.

```
$ git checkout issue3
Switched to branch 'issue3'
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: Thêm giải thích pull
Using index info to reconstruct a base tree...
<stdin>:13: new blank line at EOF.
+
warning: 1 line adds whitespace errors.
Falling back to patching base and 3-way merge...
Auto-merging myfile.txt
CONFLICT (content): Merge conflict in myfile.txt
Failed to merge in the changes.
Patch failed at 0001 Thêm giải thích pull

When you have resolved this problem run "git rebase --continue".
If you would prefer to skip this patch, instead run "git rebase --skip".
To check out the original branch and stop rebasing run "git rebase --abort".
```

Giống với lúc merge, xung đột tại myfile.txt sẽ phát sinh nên hãy chỉnh sửa.

```
<<<<<<< HEAD
commit: Lưu lại trạng thái của index
=======
pull: Lấy nội dung của remote repository
>>>>>>> issue3
```
Trường hợp rebase, sau khi đã chỉnh sửa chổ xung đột thì không commit, mà hãy chỉ định lựa chọn --continue trong lệnh rebase rồi thực hiện. Giả sử nếu là trường hợp xóa bỏ chính rebase thì hãy chỉ định lựa chọn --abort.

```
$ git add myfile.txt
$ git rebase --continue
Applying: Thêm giải thích pull
```

Sau khi checkout branch master hãy thử thực hiện merge.

```
$ git checkout master
Switched to branch 'master'
$ git merge issue3
Updating 8f7aa27..96a0ff0
Fast-forward
 myfile.txt |    1 +
 1 files changed, 1 insertions(+), 0 deletions(-)
```