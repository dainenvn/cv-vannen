# Portfolio CV - Khoàng Văn Nên

## Tên dự án

**Portfolio CV cá nhân của Khoàng Văn Nên** - trang web giới thiệu bản thân, kỹ năng và các dự án Frontend.

## Mô tả

Đây là website portfolio tĩnh được xây dựng để giới thiệu Khoàng Văn Nên, sinh viên Công nghệ thông tin định hướng Frontend Developer. Giao diện hỗ trợ nhiều kích thước màn hình, có thể chạy trực tiếp trên trình duyệt hoặc được phục vụ bằng một web server tĩnh.

## Chức năng

- Giới thiệu thông tin cá nhân và định hướng nghề nghiệp.
- Hiển thị các nhóm kỹ năng và công nghệ.
- Trình bày bốn dự án mẫu: landing page, ứng dụng Todo List, bảng thông tin thời tiết và blog cá nhân.
- Điều hướng nhanh đến các phần Giới thiệu, Kỹ năng, Dự án và Liên hệ.
- Hiển thị ảnh đại diện và thiết kế responsive cho máy tính, máy tính bảng và điện thoại.

> Lưu ý: nội dung dự án được trình bày như portfolio; một số liên kết dự án hiện điều hướng về đầu trang. Website hiện không có backend hoặc chức năng gửi biểu mẫu.

## Công nghệ

- HTML5 ngữ nghĩa.
- CSS3, Flexbox, CSS Grid và media queries.
- Google Fonts: Plus Jakarta Sans và JetBrains Mono (cần kết nối Internet để tải phông chữ; nếu ngoại tuyến, trình duyệt dùng phông chữ dự phòng).
- Docker tùy chọn: Nginx Alpine để phục vụ website tĩnh.

>Dự án không sử dụng framework, không cần Node.js/npm và không có bước biên dịch.

## Yêu cầu môi trường

- Windows, macOS hoặc Linux.
- Trình duyệt web hiện đại (Chrome, Firefox, Safari hoặc Edge).
- Để mở trực tiếp: không cần cài thêm phần mềm.
- Để chạy web server cục bộ: Python 3 (tùy chọn).
- Để chạy bằng container: Docker Engine hoặc Docker Desktop đang hoạt động.
- Kết nối Internet tùy chọn để tải Google Fonts.

## Cài đặt

Tải hoặc sao chép mã nguồn về máy. Nếu dùng Git, thay `<URL-repository>` bằng địa chỉ repository thực tế:

```bash
git clone <URL-repository>
cd <ten-thu-muc-du-an>
```

Mở **thư mục dự án gốc**, nơi có `index.html`. README này nằm trong thư mục `assets/`; không chạy các lệnh bên dưới từ `assets/`.

## Cấu hình

Không cần file cấu hình, biến môi trường hay khóa API để chạy phiên bản hiện tại. Các tài nguyên được tham chiếu theo đường dẫn tương đối:

- Trang chính: `index.html`
- CSS: `assets/css/styles.css`
- Ảnh đại diện: `assets/img/avatar.jpg`

Nếu thay ảnh đại diện, giữ tên `avatar.jpg` và đặt ảnh tại `assets/img/`, hoặc cập nhật các đường dẫn ảnh tương ứng trong `index.html`. Muốn chạy ngoại tuyến hoàn toàn, có thể thay Google Fonts bằng phông chữ hệ thống trong CSS.

## Chạy thử

### Mở trực tiếp

Mở file `index.html` trong trình duyệt. Cách này không cần cài đặt thêm, phù hợp để xem nhanh.

### Windows

Mở PowerShell tại thư mục dự án gốc. Cần cài Python 3 nếu muốn chạy web server cục bộ:

```powershell
py -m http.server 8000
```

Nếu lệnh `py` không có, thử:

```powershell
python -m http.server 8000
```

Mở `http://localhost:8000` trong trình duyệt. Dừng server bằng `Ctrl+C`.

### macOS

Mở Terminal, chuyển đến thư mục dự án gốc rồi chạy:

```bash
python3 -m http.server 8000
```

Mở `http://localhost:8000` trong trình duyệt. Dừng server bằng `Ctrl+C`.

### Linux

Mở Terminal, chuyển đến thư mục dự án gốc rồi chạy:

```bash
python3 -m http.server 8000
```

Trên một số bản phân phối, nếu chưa có Python 3, hãy cài Python 3 bằng trình quản lý gói của hệ điều hành. Mở `http://localhost:8000` trong trình duyệt. Dừng server bằng `Ctrl+C`.

### Docker (Windows, macOS, Linux)

Cài và khởi động Docker Desktop (Windows/macOS) hoặc Docker Engine (Linux). Chạy lệnh từ **thư mục dự án gốc**, nơi chứa `index.html`. Lần đầu chạy, Docker sẽ tải image Nginx Alpine từ Internet.

**macOS/Linux (Terminal):**

```bash
docker run --rm --name portfolio-web -p 8080:80 -v "$PWD:/usr/share/nginx/html:ro" nginx:alpine
```

**Windows (PowerShell):**

```powershell
docker run --rm --name portfolio-web -p 8080:80 -v "${PWD}:/usr/share/nginx/html:ro" nginx:alpine
```

Mở `http://localhost:8080`. Container sẽ dừng khi nhấn `Ctrl+C`; tùy chọn `--rm` tự xóa container sau khi dừng. Không cần tạo Dockerfile vì lệnh sử dụng trực tiếp image Nginx để phục vụ các file tĩnh.

## Thông tin liên hệ

- **Họ tên:** Khoàng Văn Nên
- **Lĩnh vực:** Frontend Developer
- **Trao đổi:** Có thể liên hệ qua các kênh được cập nhật trong phần Liên hệ của portfolio.

Thông tin email, số điện thoại và hồ sơ mạng xã hội cụ thể chưa được xác định trong mã nguồn hiện tại. Hãy bổ sung thông tin liên hệ thực tế tại đây khi sẵn sàng công khai.
