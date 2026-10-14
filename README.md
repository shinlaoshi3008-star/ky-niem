# Một đoạn đường, một đời nhớ

Project HTML tĩnh, dùng được với GitHub Pages, không cần cài thư viện hoặc build. Bốn giai đoạn, hiệu ứng xuất hiện khi cuộn, album ảnh/video, nhạc theo giai đoạn và lời gửi cuối trang. Mỗi album có thể chứa 10–15 mục hoặc nhiều hơn.

## Cấu trúc

- `index.html`: giao diện, hiệu ứng và công cụ chỉnh sửa.
- `content.js`: lời kể và danh sách tệp của từng giai đoạn.
- `assets/01-lam-quen/`, `assets/02-yeu-nhau/`, `assets/03-tranh-cai/`, `assets/04-dung-lai/`: mỗi thư mục có `images`, `videos`, `music`.
- `.nojekyll`: để GitHub Pages phục vụ trực tiếp các tệp tĩnh.

## Thêm ảnh, video và nhạc vào repo

1. Chép tệp vào thư mục tương ứng. Đặt tên không dấu, không khoảng trắng, ví dụ `anh-01.jpg`, `video-01.mp4`, `nhac.mp3`.
2. Mở `content.js`. Bốn đối tượng trong `chapters` lần lượt là bốn giai đoạn.
3. Trong đối tượng giai đoạn, thêm `image` cho ảnh nền, `music` cho nhạc và các mục trong `media` cho album. Ví dụ giai đoạn đầu:

```js
"image": "assets/01-lam-quen/images/nen.jpg",
"music": "assets/01-lam-quen/music/nhac.mp3",
"media": [
  {
    "type": "image",
    "src": "assets/01-lam-quen/images/anh-01.jpg",
    "caption": "Ngày đầu mình gặp nhau…"
  },
  {
    "type": "video",
    "src": "assets/01-lam-quen/videos/video-01.mp4",
    "caption": "Một khoảnh khắc muốn giữ lại."
  }
]
```

Thêm 10–15 đối tượng vào `media` cho mỗi giai đoạn theo thứ tự muốn hiển thị. Dùng đúng tên tệp và chữ hoa/chữ thường. Đường dẫn tính từ thư mục chứa `index.html`. Không dùng đường dẫn bắt đầu bằng `/`, để trang hoạt động cả khi repo nằm dưới đường dẫn GitHub Pages.

Ảnh trong những khối kỷ niệm lớn nằm ở `memories`: thêm thuộc tính `image` vào từng mục. Ảnh mở đầu nằm ở `heroImage` của đối tượng ngoài cùng. Các thuộc tính `title`, `text`, `desc`, `letter`… là nội dung có thể sửa. Giữ đúng dấu phẩy và dấu ngoặc; `\n` là xuống dòng trong chuỗi.

Sau khi chỉnh bản gốc, tăng `revision` từ `"1"` thành `"2"`, `"3"`… để trình duyệt dùng cấu hình mới thay vì bản chỉnh riêng đã lưu trước đó.

## Chạy thử

Có thể mở trực tiếp `index.html`. Hoặc chạy trong thư mục project:

```bash
python -m http.server 8000
```

Sau đó mở `http://localhost:8000`.

Nút **Chỉnh kỷ niệm** cho phép thử ảnh/video từ máy, thêm chú thích và sắp xếp album. Những thay đổi này chỉ lưu trong trình duyệt, không tự ghi vào repo hoặc cập nhật GitHub. Để mọi người xem cùng nội dung, hãy thêm tệp vào `assets` và sửa `content.js`, rồi commit/push. **Tải HTML hoàn chỉnh** tạo bản một file; các tệp chọn từ máy được nhúng, còn đường dẫn từ repo vẫn cần đi cùng thư mục `assets`.

## Đưa lên GitHub bằng giao diện web

1. Giải nén project.
2. Tạo repository mới trên GitHub.
3. Chọn **Add file → Upload files**. Đưa các tệp và thư mục BÊN TRONG project vào repo, để `index.html` ở thư mục gốc. Khi thư mục media còn trống, GitHub có thể không giữ thư mục đó; tải thêm các tệp thật khi có.
4. Commit các tệp.
5. Vào **Settings → Pages → Build and deployment**, chọn **Deploy from a branch**, nhánh **main**, thư mục **/(root)** và **Save**.
6. Chờ GitHub hoàn tất rồi mở URL được hiển thị trong Pages.

## Đưa lên bằng Git

Tạo một repo rỗng trên GitHub, rồi chạy trong thư mục project đã giải nén:

```bash
git init
git add .
git commit -m "Create memory project"
git branch -M main
git remote add origin https://github.com/TEN_CUA_BAN/TEN_REPO.git
git push -u origin main
```

Thay `TEN_CUA_BAN` và `TEN_REPO` bằng thông tin của bạn, rồi cấu hình Pages như trên.

## Ảnh và video

Nên dùng JPG/WebP cho ảnh, MP4 H.264/AAC cho video, MP3 cho nhạc; kiểm tra thực tế trên iPhone và máy tính. Video chỉ tải khi cần và có nút phát riêng. Nhạc cần người xem bấm **Bật nhạc** một lần, đổi theo giai đoạn và tạm dừng khi video phát. Với nhiều video, nên giảm dung lượng trước khi đưa vào repo.

GitHub Pages không kế thừa quyền riêng tư của bản Site trước đó. Kiểm tra chế độ truy cập của trang và chỉ đăng những hình ảnh/nội dung mà bạn có thể chia sẻ.

## Kiểm tra đã thực hiện

Đã kiểm tra cú pháp JavaScript, cấu trúc dữ liệu bốn giai đoạn và gói ZIP. Chưa kiểm tra hiển thị trực tiếp trên điện thoại hoặc triển khai GitHub Pages của tài khoản bạn.

## Chuyển nhạc theo giai đoạn

Nhạc nhỏ dần ở cuối đoạn và lớn dần khi vào đoạn mới, cả khi cuộn ngược. Ngoài bốn giai đoạn, nhạc tắt dần. Khi cuộn nhanh, bài cũ giảm về 0 trước khi bài mới phát. Thời gian fade in khoảng 1,4 giây và fade out khoảng 1 giây; chỉnh `FADE_IN_MS` và `FADE_OUT_MS` trong `index.html` nếu cần. Nhạc vẫn cần bấm Bật nhạc.

## Giao diện quản lý media

Mở `admin.html` trong project. Chọn giai đoạn, tải nhiều ảnh/video, sửa chú thích và thứ tự; thêm ảnh nền và nhạc riêng. Bấm **Tải gói cập nhật**, giải nén và chép `content.js` cùng `assets` vào project. Giữ các tệp cũ, rồi commit/push lên GitHub. Giao diện không tự ghi vào GitHub. Tệp mới chỉ được giữ trong phiên làm việc; xuất ZIP trước khi đóng. `admin.html` có thể mở trực tiếp hoặc qua máy chủ Python như hướng dẫn trên. Đây là công cụ soạn trên máy bạn, không phải tài khoản quản trị máy chủ.
