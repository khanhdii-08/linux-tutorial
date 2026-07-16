# Linux Command Tutorial

> **Tài liệu đào tạo Linux dành cho người mới bắt đầu**
>
> Phiên bản 1.0 | Dành cho Ubuntu 22.04 / Debian

---

## 📚 Mục lục

- [Chương 1: Điều hướng thư mục](#chương-1-điều-hướng-thư-mục)
  - [ls](#ls)
  - [cd](#cd)
  - [clear](#clear)
- [Chương 2: Quản lý thư mục và file](#chương-2-quản-lý-thư-mục-và-file)
  - [mkdir](#mkdir)
  - [touch](#touch)
  - [vi](#vi)
- [Chương 3: Đọc và tìm kiếm nội dung](#chương-3-đọc-và-tìm-kiếm-nội-dung)
  - [cat](#cat)
  - [echo](#echo)
  - [tail](#tail)
  - [grep](#grep)
- [Chương 4: Sao chép và xóa](#chương-4-sao-chép-và-xóa)
  - [cp](#cp)
  - [mv](#mv)
  - [rm](#rm)
  - [rmdir](#rmdir)
- [Chương 5: Quyền truy cập](#chương-5-quyền-truy-cập)
  - [sudo](#sudo)
  - [chmod](#chmod)
  - [chown](#chown)
- [Chương 6: Công cụ hệ thống](#chương-6-công-cụ-hệ-thống)
  - [man](#man)
  - [wget](#wget)
  - [apt](#apt)
- [Chương 7: Tiến trình và mạng](#chương-7-tiến-trình-và-mạng)
  - [kill](#kill)
  - [ping](#ping)
  - [uname](#uname)
  - [passwd](#passwd)
- [Chương 8: Theo dõi tài nguyên](#chương-8-theo-dõi-tài-nguyên)
  - [top](#top)
  - [df](#df)
  - [free](#free)
- [Phụ lục](#phụ-lục)
  - [Cheat Sheet tổng hợp](#1-cheat-sheet-tổng-hợp-toàn-bộ)
  - [Các cặp lệnh dễ nhầm](#2-các-cặp-lệnh-dễ-nhầm)
  - [Workflow thực tế](#3-workflow-thực-tế)
  - [Mini Project](#4-mini-project)
  - [30 bài tập thực hành](#5-30-bài-tập-thực-hành)
  - [Đáp án](#6-đáp-án)

---

# Chương 1. Điều hướng thư mục

---

## ls

### 1. Giới thiệu

Lệnh `ls` (list) dùng để **liệt kê nội dung của thư mục**. Đây là một trong những lệnh được sử dụng nhiều nhất trong Linux, giúp bạn xem những file và thư mục con đang có ở vị trí hiện tại.

**Khi nào sử dụng:**

- Muốn kiểm tra xem trong thư mục có những gì.
- Muốn xem thông tin chi tiết về file (kích thước, quyền, ngày tạo).
- Muốn xem cả file ẩn.

**Hoạt động:** Lệnh `ls` đọc thư mục từ hệ thống file và hiển thị danh sách các entry (file, thư mục, link) ra màn hình.

---

### 2. Cú pháp

```bash
ls [options] [đường_dẫn]
```

- `options`: Các tùy chọn để thay đổi cách hiển thị (ví dụ: `-l`, `-a`).
- `đường_dẫn`: Thư mục muốn liệt kê. Nếu bỏ trống, mặc định là thư mục hiện tại.

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                                                                  | Ví dụ     |
| ------ | ---------------------------------------------------------------------------------------- | --------- |
| `-l`   | Hiển thị chi tiết (long format): quyền, số link, owner, group, kích thước, ngày giờ sửa. | `ls -l`   |
| `-a`   | Hiển thị tất cả file, bao gồm file ẩn (bắt đầu bằng dấu `.`).                            | `ls -a`   |
| `-h`   | Hiển thị kích thước ở dạng dễ đọc (KB, MB, GB) – thường đi kèm `-l`.                     | `ls -lh`  |
| `-R`   | Liệt kê đệ quy, hiển thị nội dung của tất cả thư mục con.                                | `ls -R`   |
| `-t`   | Sắp xếp theo thời gian sửa đổi, mới nhất lên đầu.                                        | `ls -lt`  |
| `-r`   | Đảo ngược thứ tự sắp xếp.                                                                | `ls -ltr` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Liệt kê thư mục hiện tại**

```bash
ls
```

Kết quả hiển thị danh sách tên file và thư mục (không bao gồm file ẩn).

---

**Ví dụ 2: Liệt kê chi tiết**

```bash
ls -l
```

Kết quả:

```
-rw-r--r-- 1 user user 1024 Aug 10 14:30 file1.txt
drwxr-xr-x 2 user user 4096 Aug 10 14:30 folder1
```

Giải thích:

- `-rw-r--r--`: Quyền truy cập.
- `1`: Số hard link.
- `user`: Owner.
- `user`: Group.
- `1024`: Kích thước (bytes).
- `Aug 10 14:30`: Ngày giờ sửa.
- `file1.txt`: Tên file.

---

**Ví dụ 3: Hiển thị cả file ẩn**

```bash
ls -a
```

Kết quả:

```
.   ..  .bashrc  file1.txt  folder1
```

Các file bắt đầu bằng `.` là file ẩn.

---

**Ví dụ 4: Kết hợp `-l` và `-h`**

```bash
ls -lh
```

Kích thước hiển thị dạng `4.0K`, `2.3M` thay vì bytes.

---

**Ví dụ 5: Liệt kê thư mục khác**

```bash
ls /var/log
```

Liệt kê nội dung của thư mục `/var/log`.

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn vừa clone một dự án NodeJS từ Git về và muốn kiểm tra cấu trúc thư mục.

```bash
cd /home/user/projects/my-node-app
ls -la
```

Kết quả sẽ hiển thị tất cả file (bao gồm `.git`, `.env`, `node_modules`) với quyền và kích thước, giúp bạn xác nhận dự án đã được tải đúng cách.

---

### 6. Những lỗi thường gặp

| Lỗi                                                  | Nguyên nhân                    | Cách sửa                                         |
| ---------------------------------------------------- | ------------------------------ | -------------------------------------------------|
| `ls: cannot access 'xxx': No such file or directory` | Đường dẫn không tồn tại.       | Kiểm tra chính tả và đường dẫn.                  |
| Không thấy file dù biết là có                        | File bị ẩn (bắt đầu bằng `.`). | Dùng `ls -a`.                                    |
| Hiển thị quá nhiều, không thấy hết                   | Thư mục có nhiều file.         | Dùng `ls \| less`, `less`, hoặc `ls -l \| head`. |

---

### 7. Best Practices

- Luôn dùng `ls -la` để xem toàn bộ thông tin.
- Kết hợp `-t` và `-r` để xem file cũ nhất trước: `ls -ltr`.
- Dùng `ls -lS` để sắp xếp theo kích thước, file lớn nhất đầu.
- Không dùng `ls` trong script để lấy danh sách file; dùng vòng lặp `for` hoặc `find` thay thế.

---

### 8. Lưu ý

- **Không** nên dùng `ls` với wildcard `*` khi có quá nhiều file (có thể gây lỗi "Argument list too long").
- File ẩn thường là file cấu hình, không nên xóa nếu không biết rõ.

---

### 9. Mẹo ghi nhớ

> **"List - Liệt kê"** – `ls` giúp bạn "list" mọi thứ trong thư mục. Hãy nhớ `-l` = "long" (chi tiết), `-a` = "all" (tất cả).

---

### 10. Tóm tắt

- `ls`: Liệt kê file/thư mục.
- `-l`: Chi tiết.
- `-a`: Bao gồm file ẩn.
- `-h`: Dễ đọc.
- Luôn sử dụng `ls -la` để kiểm tra nhanh.

---

## cd

### 1. Giới thiệu

Lệnh `cd` (change directory) dùng để **thay đổi thư mục làm việc hiện tại** trong terminal. Khi bạn mở terminal, bạn đang ở một thư mục nhất định (thường là `/home/username`). `cd` giúp bạn di chuyển đến thư mục khác.

**Khi nào sử dụng:**

- Muốn di chuyển vào một thư mục để làm việc.
- Muốn quay về thư mục chính (home) hoặc thư mục trước đó.

**Hoạt động:** Lệnh `cd` thay đổi biến môi trường `PWD` (Print Working Directory) để terminal biết vị trí hiện tại.

---

### 2. Cú pháp

```bash
cd [đường_dẫn]
```

- `đường_dẫn`: Thư mục đích. Có thể là tuyệt đối (bắt đầu từ `/`) hoặc tương đối (từ vị trí hiện tại).

---

### 3. Các Option thường dùng

`cd` có rất ít option. Một số shell hỗ trợ:

| Option | Ý nghĩa                   |
| ------ | ------------------------- |
| `-`    | Quay về thư mục trước đó. |
| `~`    | Về thư mục home của user. |
| `..`   | Lên một cấp thư mục cha.  |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Di chuyển vào thư mục con**

```bash
cd Documents
```

Giả sử đang ở `/home/user`, lệnh này đưa bạn đến `/home/user/Documents`.

---

**Ví dụ 2: Di chuyển bằng đường dẫn tuyệt đối**

```bash
cd /var/log
```

Đưa bạn đến `/var/log` bất kể bạn đang ở đâu.

---

**Ví dụ 3: Về thư mục home**

```bash
cd ~
# hoặc
cd
```

---

**Ví dụ 4: Lên thư mục cha**

```bash
cd ..
```

Từ `/home/user/Documents`, lệnh này đưa bạn về `/home/user`.

---

**Ví dụ 5: Quay về thư mục trước đó**

```bash
cd -
```

Lệnh này chuyển bạn qua lại giữa hai thư mục.

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn đang ở thư mục `/home/user/projects/frontend`, cần chạy lệnh build backend ở `/home/user/projects/backend`.

```bash
cd ../backend
```

Di chuyển lên một cấp (đến `projects`) rồi vào `backend`.

Hoặc:

```bash
cd /home/user/projects/backend
```

---

### 6. Những lỗi thường gặp

| Lỗi                                        | Nguyên nhân                      | Cách sửa                         |
| ------------------------------------------ | -------------------------------- | -------------------------------- |
| `bash: cd: xxx: No such file or directory` | Thư mục không tồn tại.           | Kiểm tra đường dẫn.              |
| `cd: Permission denied`                    | Không có quyền truy cập thư mục. | Dùng `sudo` hoặc kiểm tra quyền. |
| Không thấy thay đổi                        | Có thể bạn đang trong subshell.  | Thoát subshell hoặc dùng `exec`. |

---

### 7. Best Practices

- Sử dụng `cd -` để chuyển nhanh giữa hai thư mục.
- Tạo alias cho các đường dẫn dài: `alias cdp='cd /var/www/project'`.
- Dùng tab để tự động hoàn thành đường dẫn.

---

### 8. Lưu ý

- `cd` chỉ ảnh hưởng đến shell hiện tại, không ảnh hưởng đến các terminal khác.
- Trong script, nếu bạn dùng `cd`, nó sẽ thay đổi thư mục của script đó.

---

### 9. Mẹo ghi nhớ

> **"Change Directory"** – `cd` là "đổi thư mục". Nhớ `cd ..` là đi lên, `cd ~` là về nhà.

---

### 10. Tóm tắt

- `cd <đường_dẫn>`: Di chuyển đến thư mục.
- `cd` hoặc `cd ~`: Về home.
- `cd ..`: Lên một cấp.
- `cd -`: Quay lại thư mục cũ.

---

## clear

### 1. Giới thiệu

Lệnh `clear` dùng để **xóa sạch màn hình terminal**, giúp bạn có một giao diện sạch sẽ để làm việc. Nó không xóa lịch sử lệnh, chỉ xóa nội dung hiển thị.

**Khi nào sử dụng:**

- Màn hình quá nhiều thông tin, khó nhìn.
- Muốn bắt đầu một phiên làm việc mới gọn gàng.

**Hoạt động:** Lệnh này gửi tín hiệu xóa màn hình (escape sequence) đến terminal.

---

### 2. Cú pháp

```bash
clear
```

Không có option hay argument.

---

### 3. Các Option thường dùng

Không có option đặc biệt. Một số terminal hỗ trợ `Ctrl+L` để làm tương tự.

---

### 4. Ví dụ cơ bản

```bash
clear
```

Màn hình sẽ trống, chỉ còn dấu nhắc lệnh.

---

### 5. Ví dụ thực tế

Sau khi chạy `ls -laR` trên một thư mục lớn, màn hình tràn ngập dữ liệu. Gõ `clear` để làm sạch.

---

### 6. Những lỗi thường gặp

Không có lỗi đặc biệt. Nếu không hoạt động, terminal của bạn có thể không hỗ trợ escape sequence.

---

### 7. Best Practices

- Dùng `Ctrl+L` thay vì gõ `clear` để nhanh hơn.
- Nếu muốn xóa lịch sử terminal, dùng `reset`.

---

### 8. Lưu ý

- `clear` không xóa lịch sử lệnh (bạn vẫn có thể dùng phím lên/xuống để xem lại).
- Một số người dùng `clear && ls -la` để làm sạch và liệt kê ngay.

---

### 9. Mẹo ghi nhớ

> **"Clear screen"** – `clear` xóa màn hình, giống như "xóa bảng" trong lớp học.

---

### 10. Tóm tắt

- `clear`: Xóa màn hình terminal.
- Phím tắt: `Ctrl+L`.

---

## Tổng kết chương 1

Chương này đã giới thiệu ba lệnh cơ bản nhất để điều hướng và làm việc với terminal:

- `ls` – Liệt kê nội dung.
- `cd` – Di chuyển giữa các thư mục.
- `clear` – Làm sạch màn hình.

Đây là những lệnh bạn sẽ sử dụng hàng trăm lần mỗi ngày.

---

## Cheat Sheet chương 1

| Lệnh             | Công dụng            |
| ---------------- | -------------------- |
| `ls`             | Liệt kê file/thư mục |
| `ls -l`          | Chi tiết             |
| `ls -a`          | Bao gồm file ẩn      |
| `ls -lh`         | Kích thước dễ đọc    |
| `cd <đường_dẫn>` | Đổi thư mục          |
| `cd ..`          | Lên cha              |
| `cd ~`           | Về home              |
| `cd -`           | Về thư mục cũ        |
| `clear`          | Xóa màn hình         |

---

## Bài tập thực hành chương 1

1. Mở terminal, dùng `ls` để xem thư mục hiện tại có gì.
2. Dùng `ls -la` để xem chi tiết, bao gồm file ẩn.
3. Di chuyển vào thư mục `/tmp` bằng `cd /tmp`.
4. Từ `/tmp`, di chuyển về thư mục home bằng `cd`.
5. Dùng `cd -` để quay lại `/tmp`.
6. Dùng `clear` để làm sạch màn hình.

---

# Chương 2. Quản lý thư mục và file

---

## mkdir

### 1. Giới thiệu

Lệnh `mkdir` (make directory) dùng để **tạo thư mục mới**. Đây là cách cơ bản nhất để tổ chức file trong Linux.

**Khi nào sử dụng:**

- Cần tạo một thư mục mới để chứa dữ liệu, dự án, hoặc tổ chức công việc.

**Hoạt động:** Lệnh này gọi hệ thống để tạo một entry mới trong hệ thống file với tên và đường dẫn chỉ định.

---

### 2. Cú pháp

```bash
mkdir [options] [tên_thư_mục]
```

- `tên_thư_mục`: Tên của thư mục cần tạo.

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                        | Ví dụ                |
| ------ | ---------------------------------------------- | -------------------- |
| `-p`   | Tạo cả thư mục cha nếu chưa tồn tại (parents). | `mkdir -p a/b/c`     |
| `-m`   | Đặt quyền truy cập cho thư mục ngay khi tạo.   | `mkdir -m 755 mydir` |
| `-v`   | Hiển thị thông báo chi tiết (verbose).         | `mkdir -v newfolder` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Tạo thư mục đơn**

```bash
mkdir project
```

Tạo thư mục `project` trong thư mục hiện tại.

---

**Ví dụ 2: Tạo nhiều thư mục cùng lúc**

```bash
mkdir src bin docs
```

Tạo ba thư mục: `src`, `bin`, `docs`.

---

**Ví dụ 3: Tạo cấu trúc thư mục lồng nhau**

```bash
mkdir -p project/src/main/java
```

Tạo toàn bộ cây thư mục nếu chưa tồn tại.

---

**Ví dụ 4: Tạo thư mục với quyền cụ thể**

```bash
mkdir -m 700 secret
```

Tạo thư mục `secret` chỉ có owner đọc/ghi/truy cập.

---

**Ví dụ 5: Tạo thư mục với thông báo**

```bash
mkdir -v myfolder
```

Kết quả:

```
mkdir: created directory 'myfolder'
```

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn bắt đầu một dự án Java và cần cấu trúc thư mục chuẩn.

```bash
mkdir -p my-java-app/src/main/java/com/myapp
mkdir -p my-java-app/src/test/java/com/myapp
mkdir -p my-java-app/target
mkdir -p my-java-app/config
```

---

### 6. Những lỗi thường gặp

| Lỗi                                                 | Nguyên nhân                                   | Cách sửa                            |
| --------------------------------------------------- | --------------------------------------------- | ----------------------------------- |
| `mkdir: cannot create directory 'xxx': File exists` | Thư mục đã tồn tại.                           | Dùng `-p` để bỏ qua hoặc xóa cũ.    |
| `Permission denied`                                 | Không có quyền ghi ở thư mục cha.             | Dùng `sudo` hoặc chọn thư mục khác. |
| `No such file or directory`                         | Thư mục cha không tồn tại và không dùng `-p`. | Dùng `mkdir -p`.                    |

---

### 7. Best Practices

- Luôn dùng `-p` khi tạo cấu trúc thư mục phức tạp để tránh lỗi.
- Đặt tên thư mục không có dấu cách, sử dụng dấu gạch dưới hoặc gạch ngang.
- Dùng `-v` trong script để log quá trình tạo thư mục.

---

### 8. Lưu ý

- Tên thư mục phân biệt chữ hoa/thường: `Project` và `project` là khác nhau.
- Không nên tạo thư mục có tên bắt đầu bằng dấu `.` trừ khi muốn ẩn.

---

### 9. Mẹo ghi nhớ

> **"Make Directory"** – `mkdir` nghĩa là "làm thư mục". Nhớ `-p` = "parents" để tạo cả cha.

---

### 10. Tóm tắt

- `mkdir <tên>`: Tạo thư mục.
- `-p`: Tạo cả thư mục cha.
- `-m`: Đặt quyền.
- `-v`: Chi tiết.

---

## touch

### 1. Giới thiệu

Lệnh `touch` dùng để **tạo file mới rỗng** hoặc **cập nhật thời gian truy cập/sửa đổi** của file đã có.

**Khi nào sử dụng:**

- Tạo file trống để chuẩn bị nội dung.
- Cập nhật timestamp của file (ví dụ: để trigger build).

**Hoạt động:** Nếu file chưa tồn tại, `touch` tạo một file rỗng. Nếu đã tồn tại, nó cập nhật thời gian sửa đổi thành thời điểm hiện tại.

---

### 2. Cú pháp

```bash
touch [options] [tên_file]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                                   | Ví dụ                            |
| ------ | --------------------------------------------------------- | -------------------------------- |
| `-c`   | Không tạo file nếu chưa tồn tại (chỉ cập nhật timestamp). | `touch -c existing.txt`          |
| `-t`   | Đặt timestamp cụ thể (YYYYMMDDhhmm.ss).                   | `touch -t 202501011200 file.txt` |
| `-r`   | Lấy timestamp từ file khác.                               | `touch -r source.txt dest.txt`   |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Tạo file rỗng**

```bash
touch README.md
```

Tạo file `README.md` trống.

---

**Ví dụ 2: Tạo nhiều file**

```bash
touch file1.txt file2.txt file3.txt
```

---

**Ví dụ 3: Cập nhật timestamp của file**

```bash
touch existing_file.log
```

Thời gian sửa đổi của `existing_file.log` được cập nhật thành hiện tại.

---

**Ví dụ 4: Cập nhật timestamp nhưng không tạo mới**

```bash
touch -c config.ini
```

Nếu `config.ini` tồn tại, cập nhật thời gian; nếu không, không làm gì.

---

**Ví dụ 5: Đặt timestamp cụ thể**

```bash
touch -t 202512312359.59 newyear.txt
```

Đặt thời gian sửa đổi của `newyear.txt` là 23:59:59 ngày 31/12/2025.

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn đang làm việc với một ứng dụng NodeJS, cần tạo file `.env` để chứa biến môi trường.

```bash
touch .env
```

Sau đó dùng `vi .env` để thêm nội dung.

---

### 6. Những lỗi thường gặp

| Lỗi                                                    | Nguyên nhân                | Cách sửa                    |
| ------------------------------------------------------ | -------------------------- | --------------------------- |
| `touch: cannot touch 'xxx': Permission denied`         | Không có quyền ghi.        | Dùng `sudo` hoặc đổi quyền. |
| `touch: cannot touch 'xxx': No such file or directory` | Thư mục cha không tồn tại. | Tạo thư mục trước.          |

---

### 7. Best Practices

- Dùng `touch` kết hợp với `mkdir -p` để tạo file trong cấu trúc thư mục.
- Dùng `touch -t` để giả lập thời gian cho mục đích kiểm thử.
- Trong script, dùng `touch -c` để an toàn hơn.

---

### 8. Lưu ý

- `touch` không thêm nội dung vào file, chỉ tạo file rỗng.
- Nếu file đã có nội dung, `touch` sẽ giữ nguyên nội dung, chỉ thay đổi thời gian.

---

### 9. Mẹo ghi nhớ

> **"Touch"** – chạm vào file để tạo mới hoặc đánh dấu thời gian.

---

### 10. Tóm tắt

- `touch <file>`: Tạo file rỗng hoặc cập nhật timestamp.
- `-c`: Không tạo mới.
- `-t`: Đặt timestamp cụ thể.

---

## vi

### 1. Giới thiệu

`vi` (hoặc `vim` – Vi Improved) là **trình soạn thảo văn bản mạnh mẽ** có sẵn trên hầu hết các hệ thống Linux. Nó hoạt động hoàn toàn trong terminal, không cần GUI.

**Khi nào sử dụng:**

- Chỉnh sửa file cấu hình.
- Viết code hoặc script nhanh.
- Khi không có GUI hoặc làm việc qua SSH.

**Hoạt động:** `vi` có hai chế độ chính:

- **Command mode:** Mặc định khi mở, dùng để di chuyển, xóa, copy, paste.
- **Insert mode:** Để nhập văn bản. Vào bằng phím `i`, thoát bằng `Esc`.

---

### 2. Cú pháp

```bash
vi [tên_file]
```

Nếu file chưa tồn tại, `vi` sẽ tạo mới.

---

### 3. Các Option thường dùng

| Option       | Ý nghĩa                       |
| ------------ | ----------------------------- |
| `+<số_dòng>` | Mở file tại dòng chỉ định.    |
| `-R`         | Mở file ở chế độ chỉ đọc.     |
| `-c <lệnh>`  | Thực thi lệnh Vim sau khi mở. |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Mở file để chỉnh sửa**

```bash
vi /etc/hosts
```

**Ví dụ 2: Mở file và đến dòng 20**

```bash
vi +20 script.sh
```

**Ví dụ 3: Mở file ở chế độ chỉ đọc**

```bash
vi -R /etc/passwd
```

---

### 5. Ví dụ thực tế

**Tình huống:** Cần sửa file cấu hình Nginx.

```bash
sudo vi /etc/nginx/nginx.conf
```

Sau đó:

1. Nhấn `i` để vào Insert mode.
2. Sửa nội dung.
3. Nhấn `Esc` để thoát Insert mode.
4. Gõ `:wq` để lưu và thoát.

---

### 6. Những lỗi thường gặp

| Lỗi                               | Nguyên nhân         | Cách sửa                                                |
| --------------------------------- | ------------------- | ------------------------------------------------------- |
| Không biết thoát                  | Đang ở Insert mode. | Nhấn `Esc`, rồi `:q!` để thoát không lưu, `:wq` để lưu. |
| `E45: 'readonly' option is set`   | File chỉ đọc.       | Thoát và mở với `sudo` hoặc `:w!` nếu có quyền.         |
| `E37: No write since last change` | Chưa lưu.           | Dùng `:w` để lưu hoặc `:q!` để bỏ qua.                  |

---

### 7. Best Practices

- Học các phím di chuyển cơ bản: `h` (trái), `j` (xuống), `k` (lên), `l` (phải).
- Dùng `dd` để xóa dòng, `yy` để copy, `p` để paste.
- Dùng `:set number` để hiển thị số dòng.
- Dùng `:wq` để lưu và thoát, `:q!` để thoát không lưu.

---

### 8. Lưu ý

- `vi` khá khó dùng cho người mới, nhưng rất mạnh mẽ. Hãy kiên nhẫn.
- Có thể dùng `nano` để đơn giản hơn nếu không cần nhiều tính năng.

---

### 9. Mẹo ghi nhớ

> **"vi"** – nhớ `i` để insert, `Esc` để thoát chế độ gõ, `:wq` để "write and quit".

---

### 10. Tóm tắt

- `vi <file>`: Mở file.
- `i`: Vào chế độ chèn.
- `Esc`: Thoát chế độ chèn.
- `:wq`: Lưu và thoát.
- `:q!`: Thoát không lưu.

---

## Tổng kết chương 2

Chương này hướng dẫn các lệnh cơ bản để tạo và chỉnh sửa file/thư mục:

- `mkdir` – Tạo thư mục.
- `touch` – Tạo file rỗng.
- `vi` – Trình soạn thảo.

---

## Cheat Sheet chương 2

| Lệnh              | Công dụng              |
| ----------------- | ---------------------- |
| `mkdir <tên>`     | Tạo thư mục            |
| `mkdir -p a/b/c`  | Tạo cấu trúc lồng nhau |
| `touch <file>`    | Tạo file rỗng          |
| `touch -c <file>` | Chỉ cập nhật timestamp |
| `vi <file>`       | Mở file với vi         |
| `i`               | Insert mode trong vi   |
| `Esc`             | Thoát Insert mode      |
| `:wq`             | Lưu và thoát vi        |
| `:q!`             | Thoát không lưu        |

---

## Bài tập thực hành chương 2

1. Tạo thư mục `linux_practice` trong home.
2. Trong đó tạo các thư mục con: `src`, `docs`, `backup`.
3. Tạo file `README.md` trong `docs`.
4. Dùng `vi` để thêm nội dung: "# Linux Practice Project".
5. Tạo file `.gitignore` trong thư mục gốc.
6. Sử dụng `touch -t` để đặt timestamp cho một file.

---

# Chương 3. Đọc và tìm kiếm nội dung

---

## cat

### 1. Giới thiệu

Lệnh `cat` (concatenate) dùng để **đọc và hiển thị nội dung của file** ra màn hình. Đây là cách nhanh nhất để xem nội dung file nhỏ.

**Khi nào sử dụng:**

- Xem nội dung file cấu hình, log, script.
- Kết hợp nhiều file lại với nhau.
- Tạo file mới từ terminal.

**Hoạt động:** `cat` đọc tuần tự từng file và in ra stdout.

---

### 2. Cú pháp

```bash
cat [options] [tên_file]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                         | Ví dụ             |
| ------ | ------------------------------- | ----------------- |
| `-n`   | Đánh số dòng.                   | `cat -n file.txt` |
| `-b`   | Đánh số dòng không rỗng.        | `cat -b file.txt` |
| `-E`   | Hiển thị `$` ở cuối mỗi dòng.   | `cat -E file.txt` |
| `-T`   | Hiển thị tab là `^I`.           | `cat -T file.txt` |
| `-s`   | Nén nhiều dòng trống thành một. | `cat -s file.txt` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xem nội dung file**

```bash
cat /etc/os-release
```

Hiển thị thông tin về hệ điều hành.

---

**Ví dụ 2: Xem nhiều file cùng lúc**

```bash
cat file1.txt file2.txt
```

Hiển thị nội dung của cả hai file liên tiếp.

---

**Ví dụ 3: Ghép hai file thành một**

```bash
cat file1.txt file2.txt > combined.txt
```

Tạo `combined.txt` chứa nội dung của cả hai.

---

**Ví dụ 4: Tạo file mới từ terminal**

```bash
cat > newfile.txt
```

Nhập nội dung, nhấn `Ctrl+D` để kết thúc.

---

**Ví dụ 5: Đánh số dòng**

```bash
cat -n script.sh
```

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn muốn xem nội dung file `package.json` của dự án NodeJS để kiểm tra dependencies.

```bash
cat package.json
```

Nếu file quá dài, kết hợp với `less`:

```bash
cat package.json | less
```

---

### 6. Những lỗi thường gặp

| Lỗi                                        | Nguyên nhân         | Cách sửa                        |
| ------------------------------------------ | ------------------- | ------------------------------- |
| `cat: file.txt: No such file or directory` | File không tồn tại. | Kiểm tra đường dẫn.             |
| Hiển thị toàn bộ file quá dài              | File lớn.           | Dùng `less` hoặc `head`/`tail`. |
| `Permission denied`                        | Không có quyền đọc. | Dùng `sudo`.                    |

---

### 7. Best Practices

- Dùng `cat` cho file nhỏ (dưới 100 dòng).
- Với file lớn, dùng `less` hoặc `more`.
- Không dùng `cat` trong pipeline khi có thể dùng redirection.

---

### 8. Lưu ý

- `cat` không có chức năng tìm kiếm hoặc cuộn.
- Khi dùng `>` để ghi, nếu file đã tồn tại, nó sẽ bị ghi đè. Dùng `>>` để thêm vào cuối.

---

### 9. Mẹo ghi nhớ

> **"Concatenate"** – `cat` dùng để xem hoặc nối file. Hãy nhớ `cat` = "xem".

---

### 10. Tóm tắt

- `cat <file>`: Xem nội dung.
- `cat file1 file2 > file3`: Ghép file.
- `-n`: Đánh số dòng.
- `>`: Ghi đè, `>>`: Thêm vào cuối.

---

## echo

### 1. Giới thiệu

Lệnh `echo` dùng để **hiển thị một dòng văn bản** ra màn hình hoặc ghi vào file. Rất hữu ích trong script và cấu hình.

**Khi nào sử dụng:**

- In thông báo trong script.
- Ghi dữ liệu vào file.
- Xem giá trị biến môi trường.

**Hoạt động:** `echo` nhận một chuỗi và in ra stdout.

---

### 2. Cú pháp

```bash
echo [options] [chuỗi]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                          | Ví dụ                    |
| ------ | ------------------------------------------------ | ------------------------ |
| `-n`   | Không xuống dòng sau khi in.                     | `echo -n "Hello"`        |
| `-e`   | Cho phép sử dụng ký tự thoát (`\n`, `\t`, `\\`). | `echo -e "Line1\nLine2"` |
| `-E`   | Tắt diễn giải ký tự thoát (mặc định).            | `echo -E "Hello\nWorld"` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: In chuỗi**

```bash
echo "Hello, Linux!"
```

**Ví dụ 2: In biến**

```bash
name="John"
echo "My name is $name"
```

**Ví dụ 3: In không xuống dòng**

```bash
echo -n "Loading"
echo "... done"
```

Kết quả: `Loading... done`

---

**Ví dụ 4: Sử dụng ký tự thoát**

```bash
echo -e "First line\nSecond line\tTabbed"
```

**Ví dụ 5: Ghi vào file**

```bash
echo "export PATH=\$PATH:/opt/myapp" >> ~/.bashrc
```

Thêm dòng vào file `.bashrc`.

---

### 5. Ví dụ thực tế

**Tình huống:** Tạo file `.env` cho dự án Docker.

```bash
echo "DB_HOST=localhost" > .env
echo "DB_USER=admin" >> .env
echo "DB_PASS=secret" >> .env
```

---

### 6. Những lỗi thường gặp

| Lỗi                          | Nguyên nhân             | Cách sửa                    |
| ---------------------------- | ----------------------- | --------------------------- |
| In ra `$var` thay vì giá trị | Dùng nhầm dấu nháy đơn. | Dùng dấu nháy kép `"$var"`. |
| Không thấy ký tự thoát       | Thiếu `-e`.             | Thêm `-e`.                  |

---

### 7. Best Practices

- Luôn đặt chuỗi trong dấu nháy kép để hỗ trợ biến.
- Dùng `echo` kết hợp với `tee` để vừa in vừa ghi file.
- Trong script, dùng `printf` nếu cần định dạng phức tạp.

---

### 8. Lưu ý

- Mặc định `echo` thêm ký tự newline.
- Dùng `>>` để thêm vào cuối file, `>` để ghi đè.

---

### 9. Mẹo ghi nhớ

> **"Echo"** – giống như tiếng vang, lặp lại những gì bạn nói.

---

### 10. Tóm tắt

- `echo "text"`: In ra màn hình.
- `-n`: Không xuống dòng.
- `-e`: Bật ký tự thoát.
- `>` và `>>`: Ghi vào file.

---

## tail

### 1. Giới thiệu

Lệnh `tail` dùng để **hiển thị phần cuối của file**. Mặc định là 10 dòng cuối. Rất hữu ích để xem log file vì log thường được ghi vào cuối file.

**Khi nào sử dụng:**

- Xem log mới nhất.
- Theo dõi log real-time.

**Hoạt động:** `tail` đọc file từ cuối lên và in ra màn hình.

---

### 2. Cú pháp

```bash
tail [options] [tên_file]
```

---

### 3. Các Option thường dùng

| Option    | Ý nghĩa                                                  | Ví dụ                     |
| --------- | -------------------------------------------------------- | ------------------------- |
| `-n <số>` | Hiển thị `<số>` dòng cuối.                               | `tail -n 20 file.log`     |
| `-f`      | Theo dõi file (follow), hiển thị thêm khi file được ghi. | `tail -f /var/log/syslog` |
| `-F`      | Tương tự `-f` nhưng theo dõi cả khi file bị rotate.      | `tail -F app.log`         |
| `-q`      | Không in tên file khi có nhiều file.                     | `tail -q file1 file2`     |
| `-v`      | Luôn in tên file.                                        | `tail -v file.log`        |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xem 10 dòng cuối**

```bash
tail /var/log/syslog
```

**Ví dụ 2: Xem 20 dòng cuối**

```bash
tail -n 20 access.log
```

**Ví dụ 3: Theo dõi log real-time**

```bash
tail -f /var/log/nginx/access.log
```

Kết thúc bằng `Ctrl+C`.

---

**Ví dụ 4: Theo dõi nhiều file cùng lúc**

```bash
tail -f /var/log/syslog /var/log/auth.log
```

**Ví dụ 5: Xem dòng cuối cùng**

```bash
tail -n 1 /etc/passwd
```

---

### 5. Ví dụ thực tế

**Tình huống:** Đang debug ứng dụng web, cần theo dõi log của Nginx.

```bash
tail -f /var/log/nginx/error.log
```

Mỗi khi có request lỗi, log hiện ngay trên terminal.

---

### 6. Những lỗi thường gặp

| Lỗi                                                              | Nguyên nhân                     | Cách sửa            |
| ---------------------------------------------------------------- | ------------------------------- | ------------------- |
| `tail: cannot open 'xxx' for reading: No such file or directory` | File không tồn tại.             | Kiểm tra đường dẫn. |
| `tail: invalid number of lines`                                  | Số dòng không hợp lệ.           | Dùng số dương.      |
| Không có kết quả dù file có nội dung                             | File trống hoặc chỉ có ít dòng. | Kiểm tra file.      |

---

### 7. Best Practices

- Dùng `tail -F` thay vì `-f` khi làm việc với logrotate.
- Kết hợp `tail -f` với `grep` để lọc: `tail -f app.log | grep ERROR`.
- Sử dụng `tail -n 0 -f` để bắt đầu theo dõi từ dòng mới nhất.

---

### 8. Lưu ý

- `-f` giữ terminal cho đến khi bạn nhấn `Ctrl+C`.
- Với file lớn, `tail` rất nhanh vì chỉ đọc phần cuối.

---

### 9. Mẹo ghi nhớ

> **"Tail"** – đuôi, tức là phần cuối của file. Ngược với `head` (đầu file).

---

### 10. Tóm tắt

- `tail <file>`: Xem 10 dòng cuối.
- `-n <số>`: Số dòng.
- `-f`: Theo dõi real-time.
- `-F`: Theo dõi cả khi file rotate.

---

## grep

### 1. Giới thiệu

Lệnh `grep` (Global Regular Expression Print) dùng để **tìm kiếm văn bản trong file** hoặc đầu vào theo pattern. Đây là công cụ cực kỳ mạnh mẽ trong Linux.

**Khi nào sử dụng:**

- Tìm kiếm từ khóa trong file log.
- Lọc kết quả của lệnh khác.
- Tìm kiếm trong code.

**Hoạt động:** `grep` đọc từng dòng và in ra những dòng khớp với pattern.

---

### 2. Cú pháp

```bash
grep [options] pattern [tên_file]
```

- `pattern`: Chuỗi hoặc biểu thức chính quy.
- `tên_file`: File cần tìm (có thể nhiều file).

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                                    | Ví dụ                       |
| ----------- | ------------------------------------------ | --------------------------- |
| `-i`        | Không phân biệt chữ hoa/thường.            | `grep -i error log.txt`     |
| `-r` / `-R` | Tìm kiếm đệ quy trong thư mục.             | `grep -r "TODO" ./src`      |
| `-l`        | Chỉ in tên file có kết quả.                | `grep -l "pattern" *.txt`   |
| `-n`        | Hiển thị số dòng.                          | `grep -n "error" log.txt`   |
| `-v`        | In dòng **không** khớp.                    | `grep -v "debug" log.txt`   |
| `-c`        | Đếm số dòng khớp.                          | `grep -c "user" access.log` |
| `-w`        | Khớp toàn bộ từ, không phải một phần.      | `grep -w "host" file.txt`   |
| `-E`        | Sử dụng biểu thức chính quy mở rộng (ERE). | `grep -E "error \| warning" log.txt` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Tìm từ khóa trong file**

```bash
grep "root" /etc/passwd
```

Hiển thị các dòng chứa "root".

---

**Ví dụ 2: Không phân biệt hoa thường**

```bash
grep -i "error" /var/log/syslog
```

---

**Ví dụ 3: Tìm đệ quy trong thư mục**

```bash
grep -r "function" ./project/src
```

---

**Ví dụ 4: Đếm số lần xuất hiện**

```bash
grep -c "404" access.log
```

---

**Ví dụ 5: Lọc kết quả từ lệnh khác**

```bash
ps aux | grep python
```

Tìm các tiến trình Python.

---

### 5. Ví dụ thực tế

**Tình huống:** Tìm tất cả các file trong dự án chứa từ khóa "deprecated" để refactor.

```bash
grep -rn "deprecated" ./src --include="*.js"
```

- `-r`: đệ quy
- `-n`: hiển thị số dòng
- `--include="*.js"`: chỉ tìm trong file JS

---

### 6. Những lỗi thường gặp

| Lỗi                                         | Nguyên nhân         | Cách sửa              |
| ------------------------------------------- | ------------------- | --------------------- |
| `grep: pattern not found`                   | Không có kết quả.   | Kiểm tra pattern.     |
| `grep: filename: No such file or directory` | File không tồn tại. | Kiểm tra đường dẫn.   |
| Kết quả quá nhiều                           | Thiếu filter.       | Thêm `-w` hoặc dùng ` \| head`. |

---

### 7. Best Practices

- Luôn dùng `-i` nếu không quan tâm hoa thường.
- Dùng `-n` để biết vị trí dòng.
- Dùng `--color=auto` để tô màu kết quả (thường mặc định).
- Kết hợp `grep` với `tail -f` để theo dõi log có lọc.

---

### 8. Lưu ý

- Pattern mặc định là Basic Regular Expression (BRE). Dùng `-E` cho ERE.
- Dấu `|` trong pattern cần dùng `grep -E`.

---

### 9. Mẹo ghi nhớ

> **"grep"** – tìm kiếm. Nhớ `grep error` là tìm lỗi.

---

### 10. Tóm tắt

- `grep pattern file`: Tìm kiếm.
- `-i`: Không phân biệt hoa thường.
- `-r`: Đệ quy.
- `-n`: Số dòng.
- `-v`: Lọc loại bỏ.
- `-c`: Đếm.

---

## Tổng kết chương 3

Chương này tập trung vào các lệnh đọc và xử lý nội dung:

- `cat` – Xem toàn bộ file.
- `echo` – In văn bản.
- `tail` – Xem phần cuối, theo dõi log.
- `grep` – Tìm kiếm mạnh mẽ.

---

## Cheat Sheet chương 3

| Lệnh                      | Công dụng        |
| ------------------------- | ---------------- |
| `cat <file>`              | Xem toàn bộ file |
| `cat file1 file2 > file3` | Ghép file        |
| `echo "text"`             | In văn bản       |
| `echo "text" > file`      | Ghi vào file     |
| `tail <file>`             | Xem 10 dòng cuối |
| `tail -f <file>`          | Theo dõi log     |
| `grep pattern file`       | Tìm kiếm         |
| `grep -r pattern ./dir`   | Tìm đệ quy       |
| `ps aux \| grep process`  | Lọc tiến trình   |

---

## Bài tập thực hành chương 3

1. Dùng `cat` xem nội dung file `/etc/hostname`.
2. Tạo file `data.txt` bằng `echo`, thêm 5 dòng thông tin.
3. Dùng `cat -n` xem file với số dòng.
4. Dùng `tail -f` theo dõi file vừa tạo (trong một terminal khác, thêm dòng mới).
5. Tìm tất cả dòng chứa từ "error" trong `/var/log/syslog` (dùng `grep`).
6. Tìm đệ quy từ khóa "main" trong thư mục `src` (nếu có).

---

# Chương 4. Sao chép và xóa

---

## cp

### 1. Giới thiệu

Lệnh `cp` (copy) dùng để **sao chép file hoặc thư mục** từ nguồn đến đích.

**Khi nào sử dụng:**

- Backup file.
- Tạo bản sao để chỉnh sửa.
- Sao chép cấu hình.

**Hoạt động:** `cp` đọc file nguồn và tạo một bản sao tại đích với nội dung giống hệt.

---

### 2. Cú pháp

```bash
cp [options] nguồn đích
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                                                       | Ví dụ                       |
| ----------- | ------------------------------------------------------------- | --------------------------- |
| `-r` / `-R` | Sao chép thư mục đệ quy.                                      | `cp -r /src /dst`           |
| `-i`        | Hỏi trước khi ghi đè (interactive).                           | `cp -i file1 file2`         |
| `-u`        | Chỉ sao chép khi nguồn mới hơn đích.                          | `cp -u source.txt dest.txt` |
| `-p`        | Giữ nguyên quyền, owner, timestamp.                           | `cp -p config.conf backup/` |
| `-v`        | Hiển thị chi tiết từng file.                                  | `cp -v *.txt backup/`       |
| `-a`        | Archive mode (tương đương `-dpR`), giữ nguyên mọi thuộc tính. | `cp -a project/ backup/`    |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Sao chép file**

```bash
cp file1.txt file2.txt
```

**Ví dụ 2: Sao chép vào thư mục khác**

```bash
cp file1.txt /tmp/
```

**Ví dụ 3: Sao chép nhiều file vào thư mục**

```bash
cp file1.txt file2.txt /backup/
```

**Ví dụ 4: Sao chép thư mục**

```bash
cp -r /home/user/Documents /backup/
```

**Ví dụ 5: Sao chép với xác nhận**

```bash
cp -i important.txt backup/
```

---

### 5. Ví dụ thực tế

**Tình huống:** Backup thư mục dự án NodeJS trước khi nâng cấp.

```bash
cp -a my-app my-app-backup
```

Sao chép toàn bộ cấu trúc, giữ nguyên quyền và timestamp.

---

### 6. Những lỗi thường gặp

| Lỗi                                                               | Nguyên nhân                     | Cách sửa                    |
| ----------------------------------------------------------------- | ------------------------------- | --------------------------- |
| `cp: omitting directory 'xxx'`                                    | Quên `-r` khi sao chép thư mục. | Thêm `-r`.                  |
| `Permission denied`                                               | Không có quyền đọc/ghi.         | Dùng `sudo` hoặc đổi quyền. |
| `cp: cannot create regular file 'xxx': No such file or directory` | Thư mục đích không tồn tại.     | Tạo thư mục đích trước.     |

---

### 7. Best Practices

- Dùng `-i` để tránh ghi đè nhầm.
- Dùng `-a` để backup toàn bộ thuộc tính.
- Dùng `-u` để chỉ backup những file thay đổi.
- Kết hợp với `rsync` cho sao chép lớn qua mạng.

---

### 8. Lưu ý

- Nếu đích là thư mục, file sẽ được tạo bên trong.
- Nếu đích là file, nó sẽ bị ghi đè (trừ khi có `-i` hoặc `-n`).

---

### 9. Mẹo ghi nhớ

> **"Copy"** – `cp` sao chép. Nhớ `-r` = "recursive" cho thư mục.

---

### 10. Tóm tắt

- `cp nguồn đích`: Sao chép.
- `-r`: Sao chép thư mục.
- `-i`: Xác nhận.
- `-p`: Giữ thuộc tính.
- `-a`: Archive (backup).

---

## mv

### 1. Giới thiệu

Lệnh `mv` (move) dùng để **di chuyển hoặc đổi tên** file/thư mục.

**Khi nào sử dụng:**

- Đổi tên file.
- Di chuyển file sang thư mục khác.
- Tổ chức lại cấu trúc thư mục.

**Hoạt động:** `mv` thay đổi đường dẫn của file trong hệ thống file. Nếu nguồn và đích cùng thư mục, nó đổi tên.

---

### 2. Cú pháp

```bash
mv [options] nguồn đích
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                               | Ví dụ                    |
| ------ | ------------------------------------- | ------------------------ |
| `-i`   | Hỏi trước khi ghi đè.                 | `mv -i old.txt new.txt`  |
| `-u`   | Chỉ di chuyển khi nguồn mới hơn đích. | `mv -u file.txt backup/` |
| `-v`   | Hiển thị chi tiết.                    | `mv -v file.txt /tmp/`   |
| `-f`   | Ghi đè không hỏi.                     | `mv -f source dest`      |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Đổi tên file**

```bash
mv oldname.txt newname.txt
```

**Ví dụ 2: Di chuyển file sang thư mục khác**

```bash
mv file.txt /tmp/
```

**Ví dụ 3: Di chuyển nhiều file**

```bash
mv file1.txt file2.txt /backup/
```

**Ví dụ 4: Đổi tên thư mục**

```bash
mv project project_old
```

**Ví dụ 5: Di chuyển với xác nhận**

```bash
mv -i config.conf /etc/
```

---

### 5. Ví dụ thực tế

**Tình huống:** Đổi tên file `.env` thành `.env.local` để phân biệt môi trường.

```bash
mv .env .env.local
```

---

### 6. Những lỗi thường gặp

| Lỗi                                                         | Nguyên nhân                            | Cách sửa              |
| ----------------------------------------------------------- | -------------------------------------- | --------------------- |
| `mv: cannot move 'xxx' to 'yyy': No such file or directory` | Đường dẫn sai.                         | Kiểm tra đường dẫn.   |
| `Permission denied`                                         | Không có quyền.                        | Dùng `sudo`.          |
| `mv: target 'xxx' is not a directory`                       | Cố gắng di chuyển nhiều file vào file. | Đích phải là thư mục. |

---

### 7. Best Practices

- Dùng `-i` để an toàn.
- Dùng `mv` để đổi tên thay vì `cp` và `rm`.
- Kiểm tra đích trước khi di chuyển.

---

### 8. Lưu ý

- `mv` thực hiện atomic trên cùng một filesystem (nhanh).
- Khác với `cp`, `mv` không tốn thêm dung lượng.

---

### 9. Mẹo ghi nhớ

> **"Move"** – di chuyển hoặc đổi tên. `mv` = move.

---

### 10. Tóm tắt

- `mv nguồn đích`: Di chuyển/đổi tên.
- `-i`: Xác nhận.
- `-u`: Chỉ khi nguồn mới hơn.
- `-v`: Chi tiết.

---

## rm

### 1. Giới thiệu

Lệnh `rm` (remove) dùng để **xóa file hoặc thư mục**. Đây là lệnh nguy hiểm vì xóa vĩnh viễn (không có Recycle Bin).

**Khi nào sử dụng:**

- Xóa file không cần thiết.
- Xóa thư mục.
- Dọn dẹp hệ thống.

**Hoạt động:** `rm` gỡ bỏ link của file khỏi hệ thống file. Dữ liệu có thể được khôi phục nhưng rất khó.

---

### 2. Cú pháp

```bash
rm [options] [tên_file]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                        | Ví dụ              |
| ------ | ---------------------------------------------- | ------------------ |
| `-r`   | Xóa thư mục và nội dung bên trong (recursive). | `rm -r folder/`    |
| `-f`   | Xóa không hỏi, bỏ qua lỗi (force).             | `rm -f file.txt`   |
| `-i`   | Hỏi trước khi xóa mỗi file.                    | `rm -i *.log`      |
| `-v`   | Hiển thị chi tiết.                             | `rm -v file.txt`   |
| `-rf`  | Kết hợp recursive và force (rất nguy hiểm).    | `rm -rf /tmp/old/` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xóa file**

```bash
rm temp.txt
```

**Ví dụ 2: Xóa nhiều file**

```bash
rm *.tmp
```

**Ví dụ 3: Xóa thư mục rỗng**

```bash
rm -r emptydir
```

**Ví dụ 4: Xóa thư mục có nội dung**

```bash
rm -r project/
```

**Ví dụ 5: Xóa không hỏi**

```bash
rm -f log.txt
```

---

### 5. Ví dụ thực tế

**Tình huống:** Dọn dẹp thư mục `node_modules` để cài lại.

```bash
rm -rf node_modules
```

---

### 6. Những lỗi thường gặp

| Lỗi                                       | Nguyên nhân         | Cách sửa                    |
| ----------------------------------------- | ------------------- | --------------------------- |
| `rm: cannot remove 'xxx': Is a directory` | Quên `-r`.          | Thêm `-r`.                  |
| `Permission denied`                       | Không có quyền xóa. | Dùng `sudo`.                |
| Xóa nhầm file quan trọng                  | Không có xác nhận.  | Luôn dùng `-i` hoặc backup. |

---

### 7. Best Practices

- **Không bao giờ** dùng `rm -rf /` trừ khi bạn biết mình đang làm gì.
- Luôn dùng `-i` hoặc kiểm tra kỹ trước khi xóa.
- Dùng `ls` để xem những file sẽ xóa trước khi `rm`.
- Có thể tạo alias `alias rm='rm -i'` để tự động hỏi.

---

### 8. Lưu ý

- Xóa bằng `rm` là vĩnh viễn, không thể khôi phục từ thùng rác.
- Dùng `trash-cli` nếu muốn có thùng rác.

---

### 9. Mẹo ghi nhớ

> **"Remove"** – xóa. Nhớ `-r` = recursive, `-f` = force. Cẩn thận!

---

### 10. Tóm tắt

- `rm <file>`: Xóa file.
- `-r`: Xóa thư mục.
- `-f`: Không hỏi.
- `-i`: Hỏi trước.
- **Luôn cẩn thận.**

---

## rmdir

### 1. Giới thiệu

Lệnh `rmdir` (remove directory) dùng để **xóa thư mục rỗng**. Khác với `rm -r`, `rmdir` chỉ xóa được thư mục không chứa file hay thư mục con.

**Khi nào sử dụng:**

- Xóa thư mục rỗng một cách an toàn.

**Hoạt động:** `rmdir` kiểm tra thư mục có rỗng không, nếu rỗng thì xóa.

---

### 2. Cú pháp

```bash
rmdir [options] [tên_thư_mục]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                            | Ví dụ               |
| ------ | ---------------------------------- | ------------------- |
| `-p`   | Xóa cả thư mục cha nếu chúng rỗng. | `rmdir -p a/b/c`    |
| `-v`   | Hiển thị chi tiết.                 | `rmdir -v emptydir` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xóa thư mục rỗng**

```bash
rmdir empty_folder
```

**Ví dụ 2: Xóa nhiều thư mục rỗng**

```bash
rmdir dir1 dir2 dir3
```

**Ví dụ 3: Xóa cả cấu trúc rỗng**

```bash
rmdir -p project/src/temp
```

Nếu `temp`, `src`, `project` đều rỗng, tất cả bị xóa.

---

### 5. Ví dụ thực tế

**Tình huống:** Dọn dẹp các thư mục trống trong dự án.

```bash
rmdir -p build/tmp/cache
```

---

### 6. Những lỗi thường gặp

| Lỗi                                                  | Nguyên nhân            | Cách sửa                              |
| ---------------------------------------------------- | ---------------------- | ------------------------------------- |
| `rmdir: failed to remove 'xxx': Directory not empty` | Thư mục không rỗng.    | Dùng `rm -r` hoặc xóa nội dung trước. |
| `No such file or directory`                          | Thư mục không tồn tại. | Kiểm tra lại.                         |

---

### 7. Best Practices

- Chỉ dùng `rmdir` khi bạn chắc chắn thư mục rỗng.
- Nếu không chắc, dùng `rm -r` sau khi kiểm tra bằng `ls`.

---

### 8. Lưu ý

- `rmdir` an toàn hơn `rm -r` vì không thể xóa thư mục có nội dung.

---

### 9. Mẹo ghi nhớ

> **"Remove Directory"** – chỉ xóa thư mục rỗng. `rmdir` = "rm directory".

---

### 10. Tóm tắt

- `rmdir <dir>`: Xóa thư mục rỗng.
- `-p`: Xóa cả cha nếu rỗng.

---

## Tổng kết chương 4

Chương này giới thiệu các lệnh sao chép và xóa:

- `cp` – Sao chép.
- `mv` – Di chuyển / đổi tên.
- `rm` – Xóa file/thư mục.
- `rmdir` – Xóa thư mục rỗng.

---

## Cheat Sheet chương 4

| Lệnh               | Công dụng         |
| ------------------ | ----------------- |
| `cp nguồn đích`    | Sao chép file     |
| `cp -r nguồn đích` | Sao chép thư mục  |
| `mv nguồn đích`    | Di chuyển/đổi tên |
| `rm <file>`        | Xóa file          |
| `rm -r <dir>`      | Xóa thư mục       |
| `rmdir <dir>`      | Xóa thư mục rỗng  |

---

## Bài tập thực hành chương 4

1. Tạo file `test1.txt`, `test2.txt`.
2. Sao chép `test1.txt` thành `test1_backup.txt`.
3. Di chuyển `test2.txt` vào thư mục `backup` (tạo nếu chưa có).
4. Đổi tên `test1_backup.txt` thành `test1_old.txt`.
5. Xóa file `test1.txt`.
6. Tạo thư mục `emptydir` và xóa bằng `rmdir`.
7. Xóa toàn bộ thư mục `backup` bằng `rm -r`.

---

# Chương 5. Quyền truy cập

---

## sudo

### 1. Giới thiệu

`sudo` (superuser do) cho phép bạn **chạy lệnh với quyền của người dùng khác**, mặc định là root (superuser).

**Khi nào sử dụng:**

- Cài đặt phần mềm.
- Chỉnh sửa file hệ thống.
- Quản lý hệ thống.

**Hoạt động:** `sudo` xác thực bạn qua mật khẩu và kiểm tra quyền trong `/etc/sudoers` trước khi thực thi lệnh.

---

### 2. Cú pháp

```bash
sudo [options] [lệnh]
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                     | Ví dụ                 |
| ----------- | --------------------------- | --------------------- |
| `-u <user>` | Chạy lệnh với user khác.    | `sudo -u www-data ls` |
| `-i`        | Đăng nhập shell như root.   | `sudo -i`             |
| `-s`        | Chạy shell với quyền root.  | `sudo -s`             |
| `-l`        | Liệt kê quyền sudo của bạn. | `sudo -l`             |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Cập nhật danh sách gói**

```bash
sudo apt update
```

**Ví dụ 2: Sửa file cấu hình**

```bash
sudo vi /etc/hosts
```

**Ví dụ 3: Xem file nhạy cảm**

```bash
sudo cat /etc/shadow
```

**Ví dụ 4: Chạy lệnh với user khác**

```bash
sudo -u postgres psql
```

**Ví dụ 5: Liệt kê quyền**

```bash
sudo -l
```

---

### 5. Ví dụ thực tế

**Tình huống:** Cần khởi động lại dịch vụ Nginx.

```bash
sudo systemctl restart nginx
```

---

### 6. Những lỗi thường gặp

| Lỗi                               | Nguyên nhân               | Cách sửa                           |
| --------------------------------- | ------------------------- | ---------------------------------- |
| `user is not in the sudoers file` | User không có quyền sudo. | Thêm user vào nhóm `sudo`.         |
| `sorry, try again`                | Sai mật khẩu.             | Nhập lại đúng mật khẩu.            |
| `sudo: command not found`         | `sudo` chưa cài.          | Cài đặt sudo (nếu dùng container). |

---

### 7. Best Practices

- Chỉ dùng `sudo` khi thực sự cần thiết.
- Không dùng `sudo` với lệnh thông thường.
- Hạn chế dùng `sudo -i` để tránh ở trạng thái root.

---

### 8. Lưu ý

- Mật khẩu sudo được lưu trong bộ nhớ đệm khoảng 15 phút.
- Dùng `sudo !!` để chạy lại lệnh trước đó với sudo.

---

### 9. Mẹo ghi nhớ

> **"Superuser Do"** – làm với quyền superuser.

---

### 10. Tóm tắt

- `sudo <lệnh>`: Chạy lệnh với quyền root.
- `-u <user>`: Chạy với user khác.
- `-i`: Shell root.

---

## chmod

### 1. Giới thiệu

`chmod` (change mode) dùng để **thay đổi quyền truy cập** của file hoặc thư mục.

**Khi nào sử dụng:**

- Phân quyền cho file cấu hình.
- Cho phép file thực thi.
- Giới hạn quyền truy cập.

**Hoạt động:** `chmod` thay đổi các bit quyền trong inode của file.

---

### 2. Cú pháp

```bash
chmod [options] mode tên_file
```

Mode có thể là **symbolic** (u+rwx) hoặc **octal** (755).

---

### 3. Các Option thường dùng

| Option             | Ý nghĩa                                | Ví dụ                                  |
| ------------------ | -------------------------------------- | -------------------------------------- |
| `-R`               | Thay đổi quyền đệ quy cho thư mục con. | `chmod -R 755 folder/`                 |
| `-v`               | Chi tiết.                              | `chmod -v 644 file.txt`                |
| `--reference=file` | Lấy quyền từ file khác.                | `chmod --reference=ref.txt target.txt` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Cho phép owner đọc/ghi, group đọc, others đọc (644)**

```bash
chmod 644 file.txt
```

**Ví dụ 2: Cho owner đọc/ghi/thi hành, group và others đọc/thi hành (755)**

```bash
chmod 755 script.sh
```

**Ví dụ 3: Thêm quyền thực thi cho owner**

```bash
chmod u+x script.sh
```

**Ví dụ 4: Xóa quyền ghi cho group và others**

```bash
chmod go-w file.txt
```

**Ví dụ 5: Đệ quy toàn bộ thư mục**

```bash
chmod -R 750 project/
```

---

### 5. Ví dụ thực tế

**Tình huống:** Tạo script và muốn chạy được.

```bash
chmod +x deploy.sh
./deploy.sh
```

---

### 6. Những lỗi thường gặp

| Lỗi                                        | Nguyên nhân              | Cách sửa             |
| ------------------------------------------ | ------------------------ | -------------------- |
| `chmod: invalid mode`                      | Mode không đúng.         | Dùng định dạng đúng. |
| `Permission denied`                        | Không đủ quyền thay đổi. | Dùng `sudo`.         |
| `chmod: cannot access 'xxx': No such file` | File không tồn tại.      | Kiểm tra đường dẫn.  |

---

### 7. Best Practices

- Không dùng `777` trừ khi thực sự cần thiết.
- Dùng `755` cho thư mục và script.
- Dùng `644` cho file văn bản thông thường.
- Hạn chế quyền tối đa cần thiết.

---

### 8. Lưu ý

- Octal mode:
  - `4` = read
  - `2` = write
  - `1` = execute
  - Cộng lại: `7` = rwx, `6` = rw-, `5` = r-x, `4` = r--.
- Ba vị trí: owner, group, others.

---

### 9. Mẹo ghi nhớ

> **"Change Mode"** – thay đổi quyền. Nhớ `chmod 755` là phổ biến.

---

### 10. Tóm tắt

- `chmod 755 file`: rwxr-xr-x
- `chmod 644 file`: rw-r--r--
- `chmod +x file`: thêm thực thi
- `-R`: đệ quy

---

## chown

### 1. Giới thiệu

`chown` (change owner) dùng để **thay đổi owner và group** của file/thư mục.

**Khi nào sử dụng:**

- Chuyển quyền sở hữu dự án cho người khác.
- Sửa owner cho dịch vụ.

**Hoạt động:** `chown` thay đổi UID và GID trong inode.

---

### 2. Cú pháp

```bash
chown [options] owner[:group] tên_file
```

---

### 3. Các Option thường dùng

| Option             | Ý nghĩa                 | Ví dụ                                  |
| ------------------ | ----------------------- | -------------------------------------- |
| `-R`               | Đệ quy.                 | `chown -R user:group folder/`          |
| `-v`               | Chi tiết.               | `chown -v user file.txt`               |
| `--reference=file` | Lấy owner từ file khác. | `chown --reference=ref.txt target.txt` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Đổi owner**

```bash
chown john file.txt
```

**Ví dụ 2: Đổi owner và group**

```bash
chown john:developers file.txt
```

**Ví dụ 3: Đổi group (chỉ group)**

```bash
chown :developers file.txt
```

**Ví dụ 4: Đệ quy**

```bash
chown -R john:developers /project
```

**Ví dụ 5: Dùng sudo**

```bash
sudo chown www-data:www-data /var/www/index.html
```

---

### 5. Ví dụ thực tế

**Tình huống:** Sau khi deploy ứng dụng web, cần đổi owner cho thư mục `uploads` để web server ghi được.

```bash
sudo chown -R www-data:www-data /var/www/myapp/uploads
```

---

### 6. Những lỗi thường gặp

| Lỗi                                        | Nguyên nhân         | Cách sửa                 |
| ------------------------------------------ | ------------------- | ------------------------ |
| `chown: invalid user: 'xxx'`               | User không tồn tại. | Kiểm tra user bằng `id`. |
| `Permission denied`                        | Không đủ quyền.     | Dùng `sudo`.             |
| `chown: cannot access 'xxx': No such file` | File không tồn tại. | Kiểm tra.                |

---

### 7. Best Practices

- Chỉ dùng `sudo` khi cần thay đổi owner.
- Thay đổi owner cẩn thận để không ảnh hưởng dịch vụ.
- Dùng `chown -R` cẩn thận với số lượng file lớn.

---

### 8. Lưu ý

- Chỉ root mới có thể đổi owner của file.
- Thường dùng `chown` kết hợp với `chmod` để phân quyền đầy đủ.

---

### 9. Mẹo ghi nhớ

> **"Change Owner"** – đổi chủ sở hữu.

---

### 10. Tóm tắt

- `chown user file`: Đổi owner.
- `chown user:group file`: Đổi owner và group.
- `-R`: Đệ quy.
- Cần `sudo`.

---

## Giải thích rwx và quyền truy cập (ASCII minh họa)

### Quyền của một file

```
-rwxr-xr-- 1 user group 1024 date filename
```

Phân tích:

- **Ký tự đầu**: `-` (file) hoặc `d` (thư mục) hoặc `l` (link)
- **3 ký tự tiếp**: owner (rwx)
- **3 ký tự tiếp**: group (r-x)
- **3 ký tự cuối**: others (r--)

| Ký tự | Ý nghĩa        |
| ----- | -------------- |
| `r`   | Read           |
| `w`   | Write          |
| `x`   | Execute        |
| `-`   | Không có quyền |

### Bảng octal

| Octal | Permission | Ý nghĩa            |
| ----- | ---------- | ------------------ |
| 7     | rwx        | Đọc, ghi, thực thi |
| 6     | rw-        | Đọc, ghi           |
| 5     | r-x        | Đọc, thực thi      |
| 4     | r--        | Chỉ đọc            |
| 3     | -wx        | Ghi, thực thi      |
| 2     | -w-        | Chỉ ghi            |
| 1     | --x        | Chỉ thực thi       |
| 0     | ---        | Không quyền        |

### ASCII minh họa

```
        Owner   Group   Others
        r w x   r w x   r w x
        | | |   | | |   | | |
        | | |   | | |   | | |
        v v v   v v v   v v v
File:   - r w x r - x r - -
        └─┬─┘ └─┬─┘ └─┬─┘
          │     │     │
          │     │     └─ Others: r--
          │     └─────── Group: r-x
          └───────────── Owner: rwx
```

---

## Tổng kết chương 5

Chương này trình bày quyền truy cập:

- `sudo` – Chạy lệnh với quyền root.
- `chmod` – Thay đổi quyền (rwx, octal).
- `chown` – Thay đổi owner/group.

---

## Cheat Sheet chương 5

| Lệnh                    | Công dụng                |
| ----------------------- | ------------------------ |
| `sudo <lệnh>`           | Chạy lệnh với quyền root |
| `chmod 755 file`        | rwxr-xr-x                |
| `chmod 644 file`        | rw-r--r--                |
| `chmod +x file`         | Thêm thực thi            |
| `chown user file`       | Đổi owner                |
| `chown user:group file` | Đổi owner và group       |
| `chmod -R 755 folder`   | Đệ quy                   |

---

## Bài tập thực hành chương 5

1. Tạo file `test.sh` và dùng `chmod +x` để cho phép thực thi.
2. Dùng `ls -l` xem quyền.
3. Đổi quyền thành `644` và xem lại.
4. Tạo thư mục `secure` và phân quyền `700`.
5. Dùng `sudo` để xem file `/etc/shadow`.
6. Đổi owner của một file thành user khác (có thể dùng `sudo`).

---

# Chương 6. Công cụ hệ thống

---

## man

### 1. Giới thiệu

`man` (manual) dùng để **xem hướng dẫn sử dụng** của một lệnh. Đây là tài liệu tham khảo chính thống.

**Khi nào sử dụng:**

- Cần biết cách dùng một lệnh.
- Xem các option của lệnh.
- Tìm hiểu chi tiết.

**Hoạt động:** `man` truy xuất các trang manual từ hệ thống và hiển thị qua `less`.

---

### 2. Cú pháp

```bash
man [tên_lệnh]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                     | Ví dụ          |
| ------ | --------------------------- | -------------- |
| `-k`   | Tìm kiếm từ khóa (apropos). | `man -k copy`  |
| `-f`   | Hiển thị mô tả ngắn.        | `man -f ls`    |
| `<số>` | Xem một section cụ thể.     | `man 5 passwd` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xem hướng dẫn của `ls`**

```bash
man ls
```

**Ví dụ 2: Tìm lệnh liên quan đến "copy"**

```bash
man -k copy
```

**Ví dụ 3: Xem section 5 (file formats)**

```bash
man 5 passwd
```

---

### 5. Ví dụ thực tế

**Tình huống:** Bạn không nhớ option của `grep`.

```bash
man grep
```

Dùng `/` để tìm kiếm trong manual, `q` để thoát.

---

### 6. Những lỗi thường gặp

| Lỗi                       | Nguyên nhân             | Cách sửa                    |
| ------------------------- | ----------------------- | --------------------------- |
| `No manual entry for xxx` | Lệnh không có man page. | Tìm trên web hoặc `--help`. |
| Không tìm thấy            | Thiếu gói man.          | Cài `man-db`.               |

---

### 7. Best Practices

- Dùng `man` trước khi hỏi Google.
- Dùng `/` để tìm kiếm trong trang.
- Dùng `q` để thoát.

---

### 8. Lưu ý

- Một số lệnh dùng `--help` để xem nhanh.
- `man` có nhiều section (1: lệnh, 5: cấu hình, 8: quản trị).

---

### 9. Mẹo ghi nhớ

> **"Manual"** – sách hướng dẫn.

---

### 10. Tóm tắt

- `man <lệnh>`: Xem manual.
- `-k`: Tìm kiếm.
- `q`: Thoát.

---

## wget

### 1. Giới thiệu

`wget` dùng để **tải file từ Internet** thông qua HTTP, HTTPS, FTP.

**Khi nào sử dụng:**

- Tải phần mềm.
- Tải dữ liệu.
- Tự động hóa download.

**Hoạt động:** `wget` gửi request HTTP và lưu file về máy.

---

### 2. Cú pháp

```bash
wget [options] [URL]
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                        | Ví dụ                                            |
| ----------- | ------------------------------ | ------------------------------------------------ |
| `-O <file>` | Lưu với tên khác.              | `wget -O myfile.zip http://example.com/file.zip` |
| `-c`        | Tiếp tục tải khi bị gián đoạn. | `wget -c http://example.com/bigfile.iso`         |
| `-q`        | Chế độ im lặng (không log).    | `wget -q http://example.com/file`                |
| `-r`        | Tải đệ quy (crawl).            | `wget -r http://example.com/`                    |
| `-P <dir>`  | Lưu vào thư mục chỉ định.      | `wget -P /tmp/ http://example.com/file`          |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Tải file**

```bash
wget https://example.com/file.zip
```

**Ví dụ 2: Tải và đổi tên**

```bash
wget -O package.deb https://example.com/app.deb
```

**Ví dụ 3: Tiếp tục tải**

```bash
wget -c https://example.com/large.iso
```

**Ví dụ 4: Tải background**

```bash
wget -b https://example.com/bigfile.zip
```

**Ví dụ 5: Tải toàn bộ website**

```bash
wget -r -l 2 https://example.com/
```

---

### 5. Ví dụ thực tế

**Tình huống:** Tải file cài đặt Docker Compose.

```bash
sudo wget -O /usr/local/bin/docker-compose https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)
sudo chmod +x /usr/local/bin/docker-compose
```

---

### 6. Những lỗi thường gặp

| Lỗi                              | Nguyên nhân               | Cách sửa                       |
| -------------------------------- | ------------------------- | ------------------------------ |
| `Unable to resolve host address` | Lỗi DNS.                  | Kiểm tra kết nối mạng.         |
| `Connection refused`             | URL sai hoặc server down. | Kiểm tra URL.                  |
| `Permission denied`              | Không có quyền ghi.       | Dùng `sudo` hoặc thư mục khác. |

---

### 7. Best Practices

- Dùng `-c` cho file lớn để tránh tải lại.
- Dùng `-q` trong script để tránh log rác.
- Kiểm tra MD5 sau khi tải.

---

### 8. Lưu ý

- `wget` không có GUI, hoạt động trong terminal.
- Đối với HTTPS, cần có certificate.

---

### 9. Mẹo ghi nhớ

> **"Wget"** – web get, tải từ web.

---

### 10. Tóm tắt

- `wget URL`: Tải file.
- `-O`: Đổi tên.
- `-c`: Tiếp tục.
- `-q`: Im lặng.
- `-r`: Đệ quy.

---

## apt

### 1. Giới thiệu

`apt` (Advanced Package Tool) là **trình quản lý gói** trên Ubuntu/Debian, dùng để cài đặt, cập nhật, gỡ bỏ phần mềm.

**Khi nào sử dụng:**

- Cài đặt phần mềm mới.
- Cập nhật hệ thống.
- Gỡ bỏ phần mềm không dùng.

**Hoạt động:** `apt` làm việc với kho lưu trữ, giải quyết phụ thuộc, tải và cài gói.

---

### 2. Cú pháp

```bash
sudo apt [command] [options] [package]
```

Cần `sudo` cho hầu hết các lệnh.

---

### 3. Các lệnh con thường dùng

| Lệnh               | Ý nghĩa                         | Ví dụ                    |
| ------------------ | ------------------------------- | ------------------------ |
| `update`           | Cập nhật danh sách gói từ repo. | `sudo apt update`        |
| `upgrade`          | Nâng cấp tất cả gói đã cài.     | `sudo apt upgrade`       |
| `install <pkg>`    | Cài đặt gói.                    | `sudo apt install nginx` |
| `remove <pkg>`     | Gỡ bỏ gói (giữ file cấu hình).  | `sudo apt remove nginx`  |
| `purge <pkg>`      | Gỡ bỏ gói và file cấu hình.     | `sudo apt purge nginx`   |
| `autoremove`       | Xóa gói không còn cần thiết.    | `sudo apt autoremove`    |
| `search <keyword>` | Tìm gói.                        | `apt search python`      |
| `show <pkg>`       | Hiển thị thông tin gói.         | `apt show git`           |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Cập nhật danh sách gói**

```bash
sudo apt update
```

**Ví dụ 2: Nâng cấp hệ thống**

```bash
sudo apt upgrade -y
```

**Ví dụ 3: Cài đặt gói**

```bash
sudo apt install curl
```

**Ví dụ 4: Gỡ bỏ gói**

```bash
sudo apt remove vim
```

**Ví dụ 5: Tìm gói liên quan đến "audio"**

```bash
apt search audio
```

---

### 5. Ví dụ thực tế

**Tình huống:** Cài đặt môi trường phát triển Python.

```bash
sudo apt update
sudo apt install python3 python3-pip git
```

---

### 6. Những lỗi thường gặp

| Lỗi                                        | Nguyên nhân              | Cách sửa                              |
| ------------------------------------------ | ------------------------ | ------------------------------------- |
| `Unable to locate package`                 | Gói không có trong repo. | Thêm repo hoặc kiểm tra tên.          |
| `E: Could not get lock /var/lib/dpkg/lock` | Có tiến trình apt khác.  | Chờ hoặc kill process.                |
| `dpkg: error processing package`           | Lỗi phụ thuộc.           | Dùng `sudo apt --fix-broken install`. |

---

### 7. Best Practices

- Luôn chạy `sudo apt update` trước khi cài đặt.
- Dùng `apt install -y` để tự động đồng ý trong script.
- Dùng `apt autoremove` thường xuyên để dọn dẹp.

---

### 8. Lưu ý

- `apt` là wrapper thân thiện của `apt-get` và `apt-cache`.
- Trên các bản phân phối khác (Fedora) dùng `dnf`.

---

### 9. Mẹo ghi nhớ

> **"APT"** – Advanced Package Tool. Nhớ `update` → `upgrade` → `install`.

---

### 10. Tóm tắt

- `sudo apt update`: Cập nhật repo.
- `sudo apt upgrade`: Nâng cấp.
- `sudo apt install <pkg>`: Cài đặt.
- `sudo apt remove <pkg>`: Gỡ bỏ.
- `sudo apt autoremove`: Dọn dẹp.

---

## Tổng kết chương 6

Chương này giới thiệu các công cụ hệ thống:

- `man` – Xem hướng dẫn.
- `wget` – Tải file.
- `apt` – Quản lý gói.

---

## Cheat Sheet chương 6

| Lệnh                     | Công dụng         |
| ------------------------ | ----------------- |
| `man <lệnh>`             | Xem manual        |
| `wget URL`               | Tải file          |
| `wget -O file URL`       | Tải và đổi tên    |
| `sudo apt update`        | Cập nhật repo     |
| `sudo apt upgrade`       | Nâng cấp hệ thống |
| `sudo apt install <pkg>` | Cài gói           |
| `sudo apt remove <pkg>`  | Gỡ bỏ             |

---

## Bài tập thực hành chương 6

1. Dùng `man` để xem hướng dẫn của `wget`.
2. Tải một file từ internet (ví dụ: logo Ubuntu) bằng `wget`.
3. Cài đặt gói `htop` bằng `apt`.
4. Gỡ bỏ `htop`.
5. Cập nhật hệ thống và nâng cấp (cẩn thận).

---

# Chương 7. Tiến trình và mạng

---

## kill

### 1. Giới thiệu

`kill` dùng để **gửi tín hiệu (signal)** đến một tiến trình, thường là để kết thúc nó.

**Khi nào sử dụng:**

- Dừng một chương trình bị treo.
- Kết thúc tiến trình theo cách mềm hoặc cứng.

**Hoạt động:** `kill` gửi signal đến PID.

---

### 2. Cú pháp

```bash
kill [options] [PID]
```

---

### 3. Các Signal thường dùng

| Signal    | Số  | Ý nghĩa                                               | Ví dụ          |
| --------- | --- | ----------------------------------------------------- | -------------- |
| `SIGTERM` | 15  | Kết thúc mềm (mặc định) – tiến trình tự dọn dẹp.      | `kill PID`     |
| `SIGKILL` | 9   | Kết thúc ngay lập tức – không cho tiến trình dọn dẹp. | `kill -9 PID`  |
| `SIGINT`  | 2   | Tương tự Ctrl+C.                                      | `kill -2 PID`  |
| `SIGSTOP` | 19  | Tạm dừng tiến trình.                                  | `kill -19 PID` |
| `SIGCONT` | 18  | Tiếp tục tiến trình đã dừng.                          | `kill -18 PID` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Kết thúc tiến trình (SIGTERM)**

```bash
kill 1234
```

**Ví dụ 2: Kết thúc mạnh (SIGKILL)**

```bash
kill -9 1234
```

**Ví dụ 3: Gửi SIGINT**

```bash
kill -2 1234
```

**Ví dụ 4: Dừng tiến trình**

```bash
kill -19 1234
```

**Ví dụ 5: Tiếp tục**

```bash
kill -18 1234
```

---

### 5. Ví dụ thực tế

**Tình huống:** Một tiến trình Python chiếm nhiều CPU và không phản hồi. Tìm PID và kill.

```bash
ps aux | grep python
# Tìm PID, ví dụ 5678
kill -9 5678
```

---

### 6. Những lỗi thường gặp

| Lỗi                              | Nguyên nhân                                   | Cách sửa      |
| -------------------------------- | --------------------------------------------- | ------------- |
| `kill: (1234) - No such process` | PID không tồn tại.                            | Kiểm tra PID. |
| `Operation not permitted`        | Không có quyền kill tiến trình của user khác. | Dùng `sudo`.  |
| Tiến trình không chết dù đã kill | Có thể là zombie hoặc cần `-9`.               | Dùng `-9`.    |

---

### 7. Best Practices

- Luôn thử `kill` (SIGTERM) trước, chỉ dùng `-9` khi thực sự cần.
- Xác định PID chính xác bằng `ps` hoặc `pgrep`.
- Dùng `pkill` để kill theo tên: `pkill -f python`.

---

### 8. Lưu ý

- `kill -9` không cho tiến trình dọn dẹp tài nguyên, có thể gây lỗi.
- Zombie process không thể kill (cần kill parent).

---

### 9. Mẹo ghi nhớ

> **"Kill"** – kết thúc tiến trình. Nhớ `-9` là "chết luôn".

---

### 10. Tóm tắt

- `kill PID`: SIGTERM (mềm).
- `kill -9 PID`: SIGKILL (cứng).
- `kill -19 PID`: STOP.
- `kill -18 PID`: CONTINUE.

---

## ping

### 1. Giới thiệu

`ping` dùng để **kiểm tra kết nối mạng** đến một máy chủ khác bằng gói ICMP.

**Khi nào sử dụng:**

- Kiểm tra máy chủ có online không.
- Đo độ trễ mạng.
- Chẩn đoán kết nối.

**Hoạt động:** `ping` gửi gói ICMP Echo Request và chờ Echo Reply, tính thời gian phản hồi.

---

### 2. Cú pháp

```bash
ping [options] [hostname/IP]
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                   | Ví dụ                     |
| ----------- | ------------------------- | ------------------------- |
| `-c <số>`   | Số lần gửi.               | `ping -c 4 google.com`    |
| `-i <giây>` | Khoảng cách giữa các gói. | `ping -i 2 google.com`    |
| `-s <byte>` | Kích thước gói.           | `ping -s 1024 google.com` |
| `-W <giây>` | Thời gian chờ reply.      | `ping -W 1 google.com`    |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Ping đến Google**

```bash
ping google.com
```

Nhấn `Ctrl+C` để dừng.

**Ví dụ 2: Ping 4 gói**

```bash
ping -c 4 8.8.8.8
```

**Ví dụ 3: Ping với khoảng cách 2 giây**

```bash
ping -i 2 google.com
```

**Ví dụ 4: Ping với kích thước gói lớn**

```bash
ping -s 1500 google.com
```

**Ví dụ 5: Ping với timeout ngắn**

```bash
ping -W 1 -c 3 google.com
```

---

### 5. Ví dụ thực tế

**Tình huống:** Kiểm tra kết nối đến server của công ty.

```bash
ping -c 4 192.168.1.100
```

Nếu không có reply, kiểm tra firewall hoặc mạng.

---

### 6. Những lỗi thường gặp

| Lỗi                      | Nguyên nhân                    | Cách sửa           |
| ------------------------ | ------------------------------ | ------------------ |
| `ping: unknown host`     | Tên host không phân giải.      | Kiểm tra DNS.      |
| `Network is unreachable` | Không có kết nối mạng.         | Kiểm tra cáp/WiFi. |
| `100% packet loss`       | Server tắt hoặc firewall chặn. | Kiểm tra firewall. |

---

### 7. Best Practices

- Dùng `-c` để giới hạn số gói.
- Dùng địa chỉ IP nếu DNS có vấn đề.
- Kết hợp với `traceroute` để chẩn đoán đường đi.

---

### 8. Lưu ý

- Một số server chặn ICMP, dẫn đến ping không thành công.
- `ping` yêu cầu quyền raw socket (có sẵn cho user).

---

### 9. Mẹo ghi nhớ

> **"Ping"** – tiếng sonar, kiểm tra còn sống không.

---

### 10. Tóm tắt

- `ping <host>`: Gửi ping liên tục.
- `-c <n>`: Gửi n gói.
- `-i <s>`: Khoảng cách.

---

## uname

### 1. Giới thiệu

`uname` (Unix name) dùng để **hiển thị thông tin về hệ thống** như kernel, tên máy, kiến trúc.

**Khi nào sử dụng:**

- Xem phiên bản kernel.
- Xem kiến trúc (32-bit hay 64-bit).
- Xem tên hệ điều hành.

---

### 2. Cú pháp

```bash
uname [options]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                    | Ví dụ      |
| ------ | -------------------------- | ---------- |
| `-a`   | Hiển thị tất cả thông tin. | `uname -a` |
| `-r`   | Phiên bản kernel.          | `uname -r` |
| `-s`   | Tên kernel (mặc định).     | `uname -s` |
| `-n`   | Tên máy (hostname).        | `uname -n` |
| `-m`   | Kiến trúc máy.             | `uname -m` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Tất cả thông tin**

```bash
uname -a
```

**Ví dụ 2: Phiên bản kernel**

```bash
uname -r
```

**Ví dụ 3: Kiến trúc**

```bash
uname -m
```

**Ví dụ 4: Hostname**

```bash
uname -n
```

---

### 5. Ví dụ thực tế

**Tình huống:** Kiểm tra kernel trước khi cài driver.

```bash
uname -r
```

---

### 6. Những lỗi thường gặp

Không có lỗi đặc biệt.

---

### 7. Best Practices

- Dùng `uname -a` để có cái nhìn tổng quan.
- Kết hợp với `lsb_release -a` để xem phiên bản OS.

---

### 8. Lưu ý

- `uname` chỉ hiển thị thông tin kernel, không phải phiên bản OS.

---

### 9. Mẹo ghi nhớ

> **"Unix name"** – tên của Unix.

---

### 10. Tóm tắt

- `uname -a`: Tất cả thông tin.
- `uname -r`: Kernel.
- `uname -m`: Kiến trúc.
- `uname -n`: Hostname.

---

## passwd

### 1. Giới thiệu

`passwd` dùng để **thay đổi mật khẩu của user**.

**Khi nào sử dụng:**

- Đổi mật khẩu cá nhân.
- Đặt mật khẩu cho user mới (với sudo).
- Khóa/mở khóa user.

---

### 2. Cú pháp

```bash
passwd [options] [username]
```

---

### 3. Các Option thường dùng

| Option | Ý nghĩa                                             | Ví dụ                 |
| ------ | --------------------------------------------------- | --------------------- |
| `-l`   | Khóa (lock) tài khoản.                              | `sudo passwd -l john` |
| `-u`   | Mở khóa.                                            | `sudo passwd -u john` |
| `-d`   | Xóa mật khẩu (không cần mật khẩu để đăng nhập).     | `sudo passwd -d john` |
| `-e`   | Bắt buộc đổi mật khẩu ngay lần đăng nhập tiếp theo. | `sudo passwd -e john` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Đổi mật khẩu của chính mình**

```bash
passwd
```

**Ví dụ 2: Đổi mật khẩu cho user khác (sudo)**

```bash
sudo passwd john
```

**Ví dụ 3: Khóa tài khoản**

```bash
sudo passwd -l john
```

**Ví dụ 4: Mở khóa**

```bash
sudo passwd -u john
```

**Ví dụ 5: Xóa mật khẩu**

```bash
sudo passwd -d john
```

---

### 5. Ví dụ thực tế

**Tình huống:** Tạo user mới và đặt mật khẩu.

```bash
sudo useradd developer
sudo passwd developer
```

---

### 6. Những lỗi thường gặp

| Lỗi                                               | Nguyên nhân                             | Cách sửa                   |
| ------------------------------------------------- | --------------------------------------- | -------------------------- |
| `passwd: Authentication token manipulation error` | Không đủ quyền hoặc password file hỏng. | Dùng `sudo` hoặc sửa file. |
| `passwd: password unchanged`                      | Mật khẩu mới không đáp ứng yêu cầu.     | Chọn mật khẩu mạnh hơn.    |

---

### 7. Best Practices

- Đặt mật khẩu mạnh (ít nhất 8 ký tự, có chữ hoa, số, ký tự đặc biệt).
- Khóa tài khoản khi không sử dụng.
- Không chia sẻ mật khẩu.

---

### 8. Lưu ý

- Root có thể đổi mật khẩu bất kỳ user mà không cần mật khẩu cũ.

---

### 9. Mẹo ghi nhớ

> **"Password"** – đặt/đổi mật khẩu.

---

### 10. Tóm tắt

- `passwd`: Đổi mật khẩu của bạn.
- `sudo passwd <user>`: Đổi cho user khác.
- `-l`: Khóa.
- `-u`: Mở khóa.

---

## Tổng kết chương 7

Chương này đề cập đến tiến trình và mạng:

- `kill` – Gửi tín hiệu đến tiến trình.
- `ping` – Kiểm tra kết nối mạng.
- `uname` – Thông tin hệ thống.
- `passwd` – Quản lý mật khẩu.

---

## Cheat Sheet chương 7

| Lệnh          | Công dụng                     |
| ------------- | ----------------------------- |
| `kill PID`    | Kết thúc tiến trình (SIGTERM) |
| `kill -9 PID` | Kết thúc mạnh (SIGKILL)       |
| `ping host`   | Kiểm tra kết nối              |
| `uname -a`    | Thông tin hệ thống            |
| `passwd`      | Đổi mật khẩu                  |

---

## Bài tập thực hành chương 7

1. Mở terminal, chạy `sleep 1000` trong background (`sleep 1000 &`). Tìm PID và kill nó.
2. Ping đến `google.com` 5 lần.
3. Dùng `uname -a` để xem kernel.
4. Đổi mật khẩu của bạn bằng `passwd`.

---

# Chương 8. Theo dõi tài nguyên

---

## top

### 1. Giới thiệu

`top` hiển thị **danh sách các tiến trình đang chạy** và mức sử dụng CPU, RAM, Swap theo thời gian thực.

**Khi nào sử dụng:**

- Kiểm tra tiến trình nào đang tiêu tốn tài nguyên.
- Giám sát hệ thống.

**Hoạt động:** `top` đọc thông tin từ `/proc` và cập nhật mỗi vài giây.

---

### 2. Cú pháp

```bash
top [options]
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                           | Ví dụ                        |
| ----------- | --------------------------------- | ---------------------------- |
| `-u <user>` | Chỉ hiển thị tiến trình của user. | `top -u root`                |
| `-p <PID>`  | Chỉ hiển thị PID cụ thể.          | `top -p 1234`                |
| `-d <giây>` | Khoảng cập nhật.                  | `top -d 2`                   |
| `-b`        | Chế độ batch (xuất ra file).      | `top -b -n 1 > snapshot.txt` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Chạy top**

```bash
top
```

Phím `q` để thoát, `Shift+M` sắp xếp theo RAM, `Shift+P` sắp xếp theo CPU.

**Ví dụ 2: Chỉ hiển thị tiến trình của user**

```bash
top -u $USER
```

**Ví dụ 3: Ghi snapshot ra file**

```bash
top -b -n 1 > top.txt
```

**Ví dụ 4: Cập nhật mỗi 1 giây**

```bash
top -d 1
```

---

### 5. Ví dụ thực tế

**Tình huống:** Máy chủ chậm, kiểm tra tiến trình tốn CPU.

```bash
top
```

Nhấn `Shift+P` để sắp xếp theo CPU, tìm PID và quyết định kill nếu cần.

---

### 6. Những lỗi thường gặp

Không có lỗi đặc biệt.

---

### 7. Best Practices

- Dùng `htop` thay thế nếu có (đẹp và dễ dùng hơn).
- Dùng `top -b -n 1` để lấy dữ liệu vào script.
- Theo dõi thường xuyên để phát hiện sự cố.

---

### 8. Lưu ý

- `top` hiển thị cả tiến trình hệ thống và user.
- Load average (1, 5, 15 phút) cho thấy mức độ tải.

---

### 9. Mẹo ghi nhớ

> **"Top"** – danh sách tiến trình hàng đầu.

---

### 10. Tóm tắt

- `top`: Xem tiến trình và tài nguyên.
- `q`: Thoát.
- `Shift+P`: Sắp xếp CPU.
- `Shift+M`: Sắp xếp RAM.

---

## df

### 1. Giới thiệu

`df` (disk free) dùng để **hiển thị dung lượng sử dụng của các filesystem**.

**Khi nào sử dụng:**

- Kiểm tra dung lượng ổ đĩa.
- Xem dung lượng còn trống.

**Hoạt động:** `df` đọc thông tin filesystem từ kernel.

---

### 2. Cú pháp

```bash
df [options] [mount_point]
```

---

### 3. Các Option thường dùng

| Option    | Ý nghĩa                       | Ví dụ           |
| --------- | ----------------------------- | --------------- |
| `-h`      | Dễ đọc (GB, MB).              | `df -h`         |
| `-T`      | Hiển thị loại filesystem.     | `df -Th`        |
| `-i`      | Hiển thị inode thay vì block. | `df -i`         |
| `--total` | Hiển thị tổng.                | `df -h --total` |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xem dung lượng ổ đĩa**

```bash
df -h
```

**Ví dụ 2: Xem loại filesystem**

```bash
df -Th
```

**Ví dụ 3: Xem inode**

```bash
df -i
```

**Ví dụ 4: Chỉ xem một mount point**

```bash
df -h /dev/sda1
```

**Ví dụ 5: Tổng hợp**

```bash
df -h --total
```

---

### 5. Ví dụ thực tế

**Tình huống:** Kiểm tra dung lượng còn trống trên `/var` vì log chiếm nhiều.

```bash
df -h /var
```

---

### 6. Những lỗi thường gặp

Không có lỗi đặc biệt.

---

### 7. Best Practices

- Dùng `df -h` thường xuyên để theo dõi dung lượng.
- Kết hợp với `du` để xem thư mục nào tốn dung lượng.

---

### 8. Lưu ý

- `df` hiển thị tổng dung lượng của filesystem, không phải file.

---

### 9. Mẹo ghi nhớ

> **"Disk Free"** – dung lượng trống của đĩa.

---

### 10. Tóm tắt

- `df -h`: Xem dung lượng dễ đọc.
- `df -Th`: Kèm loại filesystem.
- `df -i`: Xem inode.

---

## free

### 1. Giới thiệu

`free` hiển thị **thông tin bộ nhớ** (RAM và Swap).

**Khi nào sử dụng:**

- Kiểm tra RAM còn trống.
- Xem Swap đang dùng bao nhiêu.

**Hoạt động:** `free` đọc từ `/proc/meminfo`.

---

### 2. Cú pháp

```bash
free [options]
```

---

### 3. Các Option thường dùng

| Option      | Ý nghĩa                | Ví dụ       |
| ----------- | ---------------------- | ----------- |
| `-h`        | Dễ đọc.                | `free -h`   |
| `-m`        | Hiển thị bằng MB.      | `free -m`   |
| `-g`        | Hiển thị bằng GB.      | `free -g`   |
| `-s <giây>` | Cập nhật liên tục.     | `free -s 2` |
| `-t`        | Hiển thị tổng (total). | `free -th`  |

---

### 4. Ví dụ cơ bản

**Ví dụ 1: Xem RAM**

```bash
free -h
```

**Ví dụ 2: Xem bằng MB**

```bash
free -m
```

**Ví dụ 3: Cập nhật mỗi 2 giây**

```bash
free -s 2
```

Nhấn `Ctrl+C` để dừng.

**Ví dụ 4: Xem tổng**

```bash
free -ht
```

---

### 5. Ví dụ thực tế

**Tình huống:** Kiểm tra RAM trước khi chạy ứng dụng Java.

```bash
free -h
```

---

### 6. Những lỗi thường gặp

Không có lỗi.

---

### 7. Best Practices

- Dùng `free -h` để dễ đọc.
- Kết hợp với `top` để xem chi tiết tiến trình dùng RAM.

---

### 8. Lưu ý

- `available` là bộ nhớ có thể sử dụng, không chỉ là `free`.
- `Swap` dùng khi RAM đầy.

---

### 9. Mẹo ghi nhớ

> **"Free"** – bộ nhớ trống.

---

### 10. Tóm tắt

- `free -h`: RAM và Swap dễ đọc.
- `-m`: MB.
- `-s <s>`: Cập nhật.

---

## Tổng kết chương 8

Chương này giới thiệu các lệnh theo dõi tài nguyên:

- `top` – Tiến trình, CPU, RAM.
- `df` – Dung lượng đĩa.
- `free` – Bộ nhớ RAM/Swap.

---

## Cheat Sheet chương 8

| Lệnh      | Công dụng           |
| --------- | ------------------- |
| `top`     | Giám sát tiến trình |
| `df -h`   | Dung lượng đĩa      |
| `free -h` | Bộ nhớ RAM/Swap     |

---

## Bài tập thực hành chương 8

1. Chạy `top` và sắp xếp theo RAM (`Shift+M`), xác định tiến trình dùng nhiều RAM nhất.
2. Dùng `df -h` để xem dung lượng từng partition.
3. Dùng `free -h` để xem RAM và Swap.
4. Chạy `free -s 1` và quan sát sự thay đổi.

---

# Phụ lục

---

## 1. Cheat Sheet tổng hợp toàn bộ

| Lệnh     | Công dụng            | Ví dụ                   |
| -------- | -------------------- | ----------------------- |
| `ls`     | Liệt kê file/thư mục | `ls -la`                |
| `cd`     | Đổi thư mục          | `cd /var/log`           |
| `clear`  | Xóa màn hình         | `clear`                 |
| `mkdir`  | Tạo thư mục          | `mkdir -p a/b/c`        |
| `touch`  | Tạo file rỗng        | `touch file.txt`        |
| `vi`     | Soạn thảo            | `vi file.txt`           |
| `cat`    | Xem nội dung         | `cat file.txt`          |
| `echo`   | In văn bản           | `echo "Hello"`          |
| `tail`   | Xem cuối file        | `tail -f log`           |
| `grep`   | Tìm kiếm             | `grep -r "error" ./`    |
| `cp`     | Sao chép             | `cp -r src dst`         |
| `mv`     | Di chuyển/đổi tên    | `mv old new`            |
| `rm`     | Xóa                  | `rm -rf folder`         |
| `rmdir`  | Xóa thư mục rỗng     | `rmdir empty`           |
| `sudo`   | Quyền root           | `sudo apt update`       |
| `chmod`  | Đổi quyền            | `chmod 755 script`      |
| `chown`  | Đổi owner            | `chown user:group file` |
| `man`    | Hướng dẫn            | `man ls`                |
| `wget`   | Tải file             | `wget URL`              |
| `apt`    | Quản lý gói          | `sudo apt install git`  |
| `kill`   | Kết thúc tiến trình  | `kill -9 PID`           |
| `ping`   | Kiểm tra mạng        | `ping google.com`       |
| `uname`  | Thông tin hệ thống   | `uname -a`              |
| `passwd` | Đổi mật khẩu         | `passwd`                |
| `top`    | Giám sát tiến trình  | `top`                   |
| `df`     | Dung lượng đĩa       | `df -h`                 |
| `free`   | Bộ nhớ               | `free -h`               |

---

## 2. Các cặp lệnh dễ nhầm

| Lệnh 1                  | Lệnh 2                     | Phân biệt                                                                                    |
| ----------------------- | -------------------------- | -------------------------------------------------------------------------------------------- |
| `cp` (copy)             | `mv` (move)                | `cp` sao chép, giữ nguyên bản gốc. `mv` di chuyển, xóa bản gốc.                              |
| `rm` (remove)           | `rmdir` (remove directory) | `rm` xóa file hoặc thư mục (có nội dung). `rmdir` chỉ xóa thư mục rỗng.                      |
| `cat` (concatenate)     | `tail` (tail)              | `cat` xem toàn bộ file. `tail` xem phần cuối (thường cho log).                               |
| `chmod` (change mode)   | `chown` (change owner)     | `chmod` đổi quyền (rwx). `chown` đổi chủ sở hữu/group.                                       |
| `touch` (touch)         | `mkdir` (make directory)   | `touch` tạo file. `mkdir` tạo thư mục.                                                       |
| `grep` (search)         | `cat` (view)               | `grep` tìm kiếm pattern. `cat` hiển thị toàn bộ nội dung.                                    |
| `top` (process monitor) | `free` (memory)            | `top` hiển thị tiến trình và CPU/RAM theo thời gian thực. `free` chỉ hiển thị RAM/Swap tĩnh. |
| `df` (disk free)        | `free` (memory free)       | `df` kiểm tra dung lượng đĩa. `free` kiểm tra bộ nhớ RAM/Swap.                               |

---

## 3. Workflow thực tế

**Tình huống:** Tạo một dự án mới, viết file README, kiểm tra và commit lên Git.

```bash
# Tạo thư mục và di chuyển vào
mkdir my-project
cd my-project

# Tạo file README
touch README.md
echo "# My Project" > README.md
echo "This is a demo project" >> README.md

# Xem nội dung
cat README.md

# Tạo file khác
touch index.js

# Liệt kê
ls -la

# Phân quyền cho script (nếu có)
chmod +x index.js

# Khởi tạo Git
git init
git add .
git commit -m "Initial commit"
```

**Giải thích từng bước:**

1. `mkdir my-project`: Tạo thư mục.
2. `cd my-project`: Di chuyển vào.
3. `touch README.md`: Tạo file rỗng.
4. `echo "# My Project" > README.md`: Ghi nội dung.
5. `cat README.md`: Kiểm tra.
6. `ls -la`: Xem tất cả file.
7. `chmod +x index.js`: Cho phép thực thi (nếu cần).
8. `git init`: Khởi tạo Git.
9. `git add .`: Thêm tất cả.
10. `git commit -m "..."`: Commit.

---

## 4. Mini Project

**Quản lý thư mục Linux hoàn chỉnh**

**Mục tiêu:** Xây dựng một cấu trúc thư mục dự án, tạo file, sao chép, di chuyển, phân quyền và kiểm tra tài nguyên.

**Các bước thực hiện:**

```bash
# 1. Tạo cấu trúc dự án
mkdir -p ~/project/{src,bin,docs,logs}

# 2. Tạo file mẫu
touch ~/project/src/main.py
touch ~/project/docs/README.md
touch ~/project/logs/app.log

# 3. Thêm nội dung
echo "print('Hello')" > ~/project/src/main.py
echo "# Project Docs" > ~/project/docs/README.md

# 4. Sao chép file
cp ~/project/src/main.py ~/project/bin/

# 5. Di chuyển file log
mv ~/project/logs/app.log ~/project/logs/app_old.log

# 6. Phân quyền
chmod 755 ~/project/src/main.py
chmod 700 ~/project/bin/
chmod 644 ~/project/docs/README.md

# 7. Kiểm tra dung lượng
df -h ~/
du -sh ~/project/

# 8. Kiểm tra RAM
free -h

# 9. Xem tiến trình liên quan
ps aux | grep python

# 10. Dọn dẹp
# rm -rf ~/project (cẩn thận)
```

**Giải thích:**

- Bước 1: Tạo cấu trúc thư mục chuẩn (src, bin, docs, logs).
- Bước 2-3: Tạo file và thêm nội dung.
- Bước 4-5: Thực hành sao chép và di chuyển.
- Bước 6: Phân quyền hợp lý.
- Bước 7-9: Giám sát tài nguyên.
- Bước 10: Dọn dẹp (tùy chọn).

---

## 5. 30 bài tập thực hành

**Mức độ dễ (1–10)**

1. Hiển thị thư mục hiện tại.
2. Liệt kê nội dung thư mục home.
3. Tạo thư mục `test` trong `/tmp`.
4. Tạo file `hello.txt` trong `test`.
5. Xóa file `hello.txt`.
6. Xóa thư mục `test`.
7. Di chuyển vào `/var/log` và xem nội dung.
8. Tìm dòng chứa "root" trong `/etc/passwd`.
9. Xem 10 dòng cuối của `/var/log/syslog`.
10. Đổi tên file `old.txt` thành `new.txt`.

**Mức độ trung bình (11–20)**

11. Sao chép toàn bộ thư mục `docs` sang `docs_backup`.
12. Thay đổi quyền của `script.sh` thành `755`.
13. Đổi owner của file về `www-data`.
14. Cài đặt gói `curl` bằng apt.
15. Tải file từ internet bằng `wget`.
16. Ping đến `8.8.8.8` 5 lần.
17. Kiểm tra phiên bản kernel.
18. Đổi mật khẩu của user (có sudo).
19. Kill một tiến trình sleep bằng `kill`.
20. Theo dõi log Nginx bằng `tail -f`.

**Mức độ khó (21–30)**

21. Tìm tất cả file trong `/etc` chứa từ "network".
22. Sử dụng `top` để xác định tiến trình CPU cao nhất.
23. Kiểm tra dung lượng còn trống của ổ đĩa.
24. Kiểm tra RAM và Swap.
25. Tạo cấu trúc thư mục `project/{src,test,doc}` và file `README.md`.
26. Backup thư mục bằng `cp -a`.
27. Đặt quyền cho tất cả file trong thư mục là `644`, thư mục là `755`.
28. Dùng `grep -r` tìm từ khóa trong code.
29. Ghi output của `df -h` vào file `disk_usage.txt`.
30. Xây dựng script tự động backup và nén thư mục.

---

## 6. Đáp án

### Bài 1–10 (Tóm tắt)

1. `pwd`
2. `ls ~`
3. `mkdir /tmp/test`
4. `touch /tmp/test/hello.txt`
5. `rm /tmp/test/hello.txt`
6. `rmdir /tmp/test` (nếu rỗng) hoặc `rm -r /tmp/test`
7. `cd /var/log && ls`
8. `grep "root" /etc/passwd`
9. `tail -n 10 /var/log/syslog`
10. `mv old.txt new.txt`

### Bài 11–20

11. `cp -r docs docs_backup`
12. `chmod 755 script.sh`
13. `sudo chown www-data file`
14. `sudo apt install curl`
15. `wget http://example.com/file`
16. `ping -c 5 8.8.8.8`
17. `uname -r`
18. `sudo passwd user`
19. `kill PID` hoặc `kill -9 PID`
20. `tail -f /var/log/nginx/access.log`

### Bài 21–30

21. `grep -r "network" /etc/`
22. `top` (Shift+P)
23. `df -h`
24. `free -h`
25. `mkdir -p project/{src,test,doc}` và `touch project/README.md`
26. `cp -a project project_backup`
27. `find . -type f -exec chmod 644 {} \;` và `find . -type d -exec chmod 755 {} \;`
28. `grep -r "TODO" ./src`
29. `df -h > disk_usage.txt`
30. Script:

```bash
#!/bin/bash
BACKUP_DIR="/backup"
mkdir -p $BACKUP_DIR
tar -czf $BACKUP_DIR/project_$(date +%Y%m%d).tar.gz ~/project
```

---

# Lời kết

Cảm ơn bạn đã đọc toàn bộ tài liệu. Đây là những kiến thức nền tảng để bạn bắt đầu hành trình làm chủ Linux. Hãy thực hành nhiều nhất có thể. Chúc bạn thành công!

**Tác giả:** Linux System Administrator & Technical Writer  
**Phiên bản:** 1.0  
**Ngày:** 2026-07-15
