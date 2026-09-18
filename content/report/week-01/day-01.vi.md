+++
title = "Ngày 01 - 17/06/2026 (on-site)"
weight = 1
+++

#### Chi tiết cách chạy các lệnh

##### 1. Khởi tạo repository cục bộ

Đầu tiên, tôi có 1 project chỉ có 1 file Project.md chứa nội dung Hello world!

Tôi sử dụng `git init` để khởi tạo một Git repository trong thư mục dự án. Sau khi thực hiện, Git tạo thư mục ẩn `.git` để lưu metadata và lịch sử phiên bản.

![1789617421926](/report/week-01/image/day-01.vi/1789617421926.png)

##### 2. Tạo repository trên GitHub và thiết lập remote

Tiếp theo, tôi đăng nhập tài khoản GitHub và bấm **New** để tạo repository mới.

![1789617470266](/report/week-01/image/day-01.vi/1789617470266.png)

Điền tên repo, để public và bấm tạo

![1789617531589](/report/week-01/image/day-01.vi/1789617531589.png)

Tôi dùng `git remote add origin` để liên kết repository cục bộ với repository trên GitHub. Sau đó dùng `git remote -v` để kiểm tra địa chỉ remote.

![1789617623214](/report/week-01/image/day-01.vi/1789617623214.png)

##### 3. Đưa thay đổi lên GitHub

Tiếp theo, tôi chạy lệnh `git add` đưa thay đổi từ working directory vào staging area để chuẩn bị cho commit.

![1789617764959](/report/week-01/image/day-01.vi/1789617764959.png)

Tiếp theo, tôi chạy lệnh `git commit` để lưu vào git history

![1789617837157](/report/week-01/image/day-01.vi/1789617837157.png)

Tôi sẽ kiểm tra branch hiện tại bằng lệnh `git branch`

![1789617885835](/report/week-01/image/day-01.vi/1789617885835.png)

Hiện tại, nhìn vào dấu sao, tôi đang đứng ở branch `master`. Tôi có thể đổi tên branch bằng lệnh `git branch -M <tên-branch-mới>`.

![1789617955822](/report/week-01/image/day-01.vi/1789617955822.png)

Tiếp theo, tôi đẩy thay đổi lên GitHub bằng lệnh `git push`.

![1789618035903](/report/week-01/image/day-01.vi/1789618035903.png)

![1789618057606](/report/week-01/image/day-01.vi/1789618057606.png)

##### 4. Clone repository với vai trò người dùng thứ hai

Bây giờ, tôi sẽ dùng `git clone` để clone project về, giả lập là người dùng thứ hai.

![1789618189005](/report/week-01/image/day-01.vi/1789618189005.png)

Thư mục clone có cả source code và git history

![1789618234642](/report/week-01/image/day-01.vi/1789618234642.png)

Bây giờ, tôi sẽ thay đổi nội dung `Project.md`, commit rồi push lên GitHub với vai trò người dùng thứ hai (trong thư mục đã clone).

![1789618846532](/report/week-01/image/day-01.vi/1789618846532.png)

![1789618421283](/report/week-01/image/day-01.vi/1789618421283.png)

##### 5. Lấy thay đổi từ remote bằng `fetch` và `pull`

Bây giờ, GitHub có commit mới mà repository cục bộ của người dùng thứ nhất chưa có.

Tôi sẽ chuyển qua thư mục của người dùng thứ nhất và chạy lệnh `git fetch origin`.

![1789618505331](/report/week-01/image/day-01.vi/1789618505331.png)

`git fetch` tải metadata, branch và commit mới từ remote về nhưng không tự động đưa thay đổi đó vào branch hiện tại.

![1789618699160](/report/week-01/image/day-01.vi/1789618699160.png)

![1789618902311](/report/week-01/image/day-01.vi/1789618902311.png)

Khác với `fetch`, `git pull` tải thay đổi từ remote và tích hợp chúng vào branch hiện tại.

![1789618941260](/report/week-01/image/day-01.vi/1789618941260.png)

![1789618956510](/report/week-01/image/day-01.vi/1789618956510.png)

Project.md đã được cập nhật

##### 6. Tạo và chuyển branch

Bây giờ, tôi tạo branch `feature-login` để phát triển chức năng đăng nhập độc lập với branch `main`.

![1789619033891](/report/week-01/image/day-01.vi/1789619033891.png)

Hiện tại, tôi đã tạo branch `feature-login` nhưng vẫn đang đứng ở branch `main` (nhìn vào dấu sao).

Tiếp theo, tôi dùng `git checkout` để chuyển branch.

![1789619104186](/report/week-01/image/day-01.vi/1789619104186.png)

##### 7. Khôi phục thay đổi chưa commit

Giờ tôi sẽ thử sửa sai nội dung file `Project.md`, sau đó dùng lệnh Git để khôi phục.

![1789619354173](/report/week-01/image/day-01.vi/1789619354173.png)

![1789619455955](/report/week-01/image/day-01.vi/1789619455955.png)

Mặc dù `git checkout` trước đây thường được dùng để chuyển branch, trong ví dụ này tôi sử dụng nó để khôi phục `Project.md` về phiên bản trong commit gần nhất và loại bỏ thay đổi chưa commit.

##### 8. Sửa commit gần nhất bằng `commit --amend`

Bây giờ tôi sẽ tạo file README.md và commit nó ở người dùng 1

![1789619757201](/report/week-01/image/day-01.vi/1789619757201.png)

tiếp theo, tôi sẽ thay đổi nội dung README.md và ghi đè commit cuối của git history

![1789619906378](/report/week-01/image/day-01.vi/1789619906378.png)

##### 9. Loại file khỏi staging area bằng `reset`

Bây giờ, tôi sẽ test lệnh git reset

![1789620093843](/report/week-01/image/day-01.vi/1789620093843.png)

Tôi dùng `git reset HEAD README.md` để loại file khỏi staging area nhưng vẫn giữ nguyên thay đổi trong working directory.

##### 10. Tạm cất thay đổi bằng `stash`

Tiếp theo, tôi sẽ test lệnh git stash

README.md có thay đổi nhưng tôi chưa muốn commit.

![1789620232022](/report/week-01/image/day-01.vi/1789620232022.png)

Tôi chưa muốn commit phần code đang làm dở nên sử dụng `git stash` để tạm cất thay đổi, đưa working directory trở lại trạng thái sạch.

![1789620311688](/report/week-01/image/day-01.vi/1789620311688.png)

Dùng lệnh git stash pop để khôi phục (lấy ra thay đổi đã stash)

![1789620438762](/report/week-01/image/day-01.vi/1789620438762.png)

##### 11. Áp dụng lại commit bằng `rebase`

Hiện tại branch feature-login đã sửa README.md và thêm login.txt nhưng branch main chưa có.

Giờ tôi chuyển qua branch main thêm new-feature và commit nó

![1789620601395](/report/week-01/image/day-01.vi/1789620601395.png)

Tôi chuyển qua lại branch feature-login và rebase main

![1789620706437](/report/week-01/image/day-01.vi/1789620706437.png)

Lúc này, lịch sử Git của `feature-login` đã thay đổi và có thêm commit `feat: update new feature`.

Git rebase giúp lịch sử commit tuyến tính hơn bằng cách áp dụng lại các commit của `feature-login` lên đầu branch `main`.

##### 12. Hợp nhất branch bằng `merge`

Sau khi chức năng login ở branch feature-login hoàn thành, tôi merge branch `feature-login` vào `main`

![1789620880413](/report/week-01/image/day-01.vi/1789620880413.png)

Lúc này, các thay đổi từ `feature-login` mà `main` chưa có (`README.md` và `login.txt`) đã được cập nhật vào `main`.

##### 13. Gộp commit bằng interactive rebase

Tôi dùng lệnh như hình để tạo branch mới và chuyển sang branch đó

![1789621099569](/report/week-01/image/day-01.vi/1789621099569.png)

![1789622885956](/report/week-01/image/day-01.vi/1789622885956.png)

Sau đó, tôi chạy `git rebase -i` để bắt đầu interactive rebase. Git sẽ mở trình soạn thảo để tôi lựa chọn cách xử lý các commit.

![1789622968826](/report/week-01/image/day-01.vi/1789622968826.png)

![1789622984259](/report/week-01/image/day-01.vi/1789622984259.png)

Tôi đổi `pick` của commit 2 và 3 thành `squash`, sau đó dùng lệnh `:wq` để lưu và thoát.

![1789623795093](/report/week-01/image/day-01.vi/1789623795093.png)

Trong màn hình chỉnh commit message, tôi giữ lại 1 nội dung commit mong muốn và xóa các commit còn lại, sau đó lưu và thoát.

![1789623905215](/report/week-01/image/day-01.vi/1789623905215.png)

Bây giờ, các commit đã được gộp thành một commit.

##### 14. Áp dụng một commit cụ thể bằng `cherry-pick`

Tiếp theo, tôi tạo branch mới `experimental` và commit file sửa lỗi.

![1789624270151](/report/week-01/image/day-01.vi/1789624270151.png)

![1789624436355](/report/week-01/image/day-01.vi/1789624436355.png)

Sau khi chạy `git cherry-pick`, commit sửa lỗi từ branch `experimental` đã được áp dụng vào branch `main`.
