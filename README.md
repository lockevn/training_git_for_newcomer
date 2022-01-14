# Guide for work

## Workstation

laptop Macbook Air

nên có màn hình ngoài

24 độ phân giải FullHD LG 24MK600M-B 23.8 inch FHD IPS 5ms 75Hz FreeSync
4350

27 độ phân giải 2K ViewSonic VX2780-2K-SHDJ 27 inch 2K IPS 75Hz HDMI DP 4ms 250cd

# B: Salary: X = 100tr

# Skill to fill

- preprocessor CSS: LESS, SaSS (shorter, reuse, variables, centralized settings and rules)
- HTML5: article, section, header, footer, aside
- SQLite:
  Tool https://sqlitebrowser.org/dl

  table
  records = row
  row contains fields (id, username, fullname)
  query
  loop in rows, select what we want
  SELECT \* FROM student // hiển thị tất cả fields trong bảng student

      SELECT id, username FROM student	// chỉ hiển thị field id và username từ bảng student

      SELECT id, username FROM student WHERE id = 1 // điều kiện là id phải = 1

      SELECT student.fullname, classroom.name FROM student JOIN classroom ON student.classid = classroom.id
      // join 2 bảng, chỉ ghép row khi (ON student.classid = classroom.id)

      SELECT student.fullname, student.age, classroom.name FROM student JOIN classroom
      ON student.classid = classroom.id
      WHERE student.age > 35
      // sau khi ghép dòng từ 2 bảng, như vD trên, thì lọc kết quả bằng WHERE, chỉ lấy các ông già trên 35 tuổi

      DELETE FROM student WHERE age > 40

      UPDATE student SET note = 'hello old men' WHERE age > 35

# - Visual Studio CODE: lightweight, and very good IDE

open folder, chú ý 2 tabs quan trọng bên trái, là Explorer
và Git (source control)
và Search

# - Git

## General: hệ thống quản lý phiên bản

ghi lại các thay đổi (tới tận từng ký tự) trên folders và files

thay đổi, ví dụ như là một quyển sổ, ghi lại các action (khi nào, ai, làm gì, thay đổi ở đâu)

12 1 2022| thach| init, create file index.html
12 1 2022| thach | them file linh tinh
12 1 2022| thach | vao sua title

UI tool: https://git-fork.com

tạo folder
mở với cmd
gõ lệnh `git init`

## Change

nếu mình change 3 files, thì quá trình tạo ra commit, là đóng gói (stage changes)
và gửi commit vào kho (repository) gọi là commit

tạo ra các thay đổi (changes)
đóng gói thay đổi (stage changes)
gửi cái gói đó vào repo (commit / tạo ra commit)

Discard (huỷ bỏ changes)

## Branch

gần giống như tạo ra một snapshot của folder trên đĩa, tại đúng điểm (=commit) đang checkout trên Git tree

khi làm feature mới, thường sẽ tạo branch mới (`feature/new_footer`) từ `master`, rồi làm việc trên branch mới đó `feature/new_footer`

nhiều người có thể cùng lúc làm việc trên nhiều branch khác nhau

Khi xong feature rồi, thì merge vào master (khi làm việc chung trong team, thì bằng cách **tạo Pull Request**, từ `feature/new_footer` vào `master`)
**tạo Pull Request** giống như là: "Anh `T` ơi, em có code mới thêm footer ở trong branch feature/new_footer, anh xem duyệt, nếu OK, thì approve PR hộ em"

### stash, thao tác trên local change

cất tạm local changes vào trong một bản nháp (gọi là stash)

## Remote repository and local repo

`L` và `T` cùng làm việc trên repo `smartcity`

1. manually, thì trên máy `T`, anh sửa và thêm mới rất nhiều
2. `T` sẽ gửi (bằng email) toàn bộ cái cây ở trạng thái mới lên github
3. `L`, lên github, download cái cây ở trạng thái mới, về máy `L`

tương đương với ==========>

1. Thach làm việc trên máy `T`
2. `T` `push` code lên Github (remote repo)
3. `L` `pull` code từ github về máy mình

### fetch

cập nhật toàn bộ cây từ remote repo cho mình "xem" (không hề ảnh hưởng tới files đang làm việc, vì files/trạng thái đang làm việc chỉ phụ thuộc vào mình đang checkout ở đâu thôi)

vì đôi khi máy mình ko refresh kịp những gì ĐÃ diễn ra trên remote repo
Nếu dùng Tool Fork, sẽ tự `fetch` khoảng 3 phút một lần, nên ít khi phải dùng command này.

### review pull request (PR)

Vào Repo, vào tab [Pull requests]
chỉ quan tâm tới 2 tab [Conversation] và [Files changed]

Comment vào các chỗ cảm thấy cần góp ý.

NếU author của PR (`T` tạo PR thì `T` là author) đã sửa theo suggestion của L, thì L resolve comment của L đi nếu đã hài lòng.
