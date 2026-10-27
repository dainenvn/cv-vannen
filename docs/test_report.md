# BÁO CÁO KIỂM THỬ

## Thông tin chung

- **Dự án:** Portfolio CV cá nhân Khoàng Văn Nên
- **Phiên bản:** 1.0
- **Ngày kiểm thử:** 27/10/2026
- **Phạm vi:** Trang portfolio tĩnh, HTML/CSS và các tài nguyên đi kèm.
- **Môi trường kiểm thử trực quan:** macOS, trình duyệt tích hợp VS Code; viewport desktop 1440 × 1000 và mobile 390 × 844.
- **Phương pháp:** Mở trang cục bộ, quan sát giao diện, kiểm tra DOM và đọc mã HTML/CSS. Đây là kiểm thử thủ công, không thay thế kiểm thử đa trình duyệt, kiểm thử bảo mật chuyên sâu hay kiểm thử triển khai production.

## Kết luận tổng quan

**Chưa nên xem phiên bản hiện tại là đạt đầy đủ để phát hành.** Trang mở được và hiển thị phần giới thiệu, nhưng phát hiện lỗi responsive ở màn hình hẹp, cấu trúc HTML bị lặp và khu vực liên hệ chưa có biểu mẫu gửi dữ liệu. Các mục Docker, triển khai production và kiểm thử đa trình duyệt chưa được thực hiện.

## 1. Tính đúng đắn

**Kết quả: Chưa đạt.**

- Trang cục bộ tải được tiêu đề và phần giao diện đầu trang; có các liên kết điều hướng đến Giới thiệu, Kỹ năng, Dự án và Liên hệ.
- Kiểm tra DOM ghi nhận hai phần tử `<main>`; mã nguồn có một tài liệu HTML thứ hai được chèn vào phần thân tài liệu đầu tiên. Đây là cấu trúc HTML không hợp lệ và có thể khiến nội dung lặp hoặc hiển thị không như dự kiến.
- Kiểm tra DOM không tìm thấy phần tử `<form>`. Các trường nhập liệu và nút SEND hiện chỉ là giao diện, chưa có xử lý gửi thông tin.
- Các nút “Xem chi tiết dự án” đang trỏ về `#top`, không mở trang chi tiết dự án.

**Minh chứng quan sát:** Trang được mở trực tiếp trong trình duyệt kiểm thử; ảnh chụp được hiển thị trong phiên làm việc nhưng hiện chưa lưu được vào workspace.

## 2. UI/UX

**Kết quả: Chưa đạt trên viewport mobile đã kiểm tra; desktop hiển thị được.**

- Ở viewport 1440 × 1000, phần đầu trang, tên, điều hướng và nội dung giới thiệu hiển thị.
- Ở viewport 390 × 844, thanh điều hướng và nội dung phần giới thiệu bị cắt theo chiều ngang; một số chữ không nằm trọn trong vùng nhìn thấy. CSS đang ẩn tràn ngang ở `body`, vì vậy phần bị tràn không thể cuộn ngang để đọc.
- Chưa kiểm tra trên nhiều kích thước trung gian, thiết bị thật, trình đọc màn hình hoặc các trình duyệt khác.

**Minh chứng quan sát:** Đã chụp giao diện ở viewport desktop và mobile trong phiên kiểm thử. Ảnh chưa có trong repository nên chưa thể đính kèm liên kết tải tại đây.

## 3. Khả năng vận hành - xử lý lỗi

**Kết quả: Đạt một phần.**

- Có thể mở trang tĩnh cục bộ; không cần backend hoặc bước biên dịch để hiển thị nội dung.
- Giao diện không có cơ chế gửi biểu mẫu, trạng thái thành công/thất bại, kiểm tra dữ liệu nhập hoặc thông báo lỗi. Mất kết nối có thể ảnh hưởng Google Fonts; phông chữ dự phòng được khai báo trong CSS nhưng chưa kiểm tra trong môi trường ngoại tuyến.
- Chưa thực hiện kiểm thử tải tài nguyên lỗi, kiểm thử mạng, hoặc xác minh các luồng tương tác ngoài điều hướng neo trang.

## 4. Bảo mật

**Kết quả: Chưa đánh giá đầy đủ; bề mặt rủi ro hiện tại thấp do website tĩnh.**

- Trong phạm vi mã nguồn đã kiểm tra, không thấy backend, xác thực người dùng, lưu trữ dữ liệu nhập hay khóa API.
- Các trường liên hệ hiện không được gửi đi vì không nằm trong biểu mẫu có xử lý. Nếu bổ sung chức năng gửi dữ liệu, cần kiểm tra và làm sạch dữ liệu đầu vào, chống spam và bảo vệ dữ liệu cá nhân.
- Google Fonts được tải từ dịch vụ bên ngoài; cần cân nhắc quyền riêng tư và yêu cầu mạng khi triển khai.
- Chưa chạy công cụ quét lỗ hổng, kiểm tra cấu hình máy chủ, HTTPS, CSP hoặc các header bảo mật. Không xem nội dung này là chứng nhận bảo mật.

## 5. Chất lượng mã nguồn

**Kết quả: Chưa đạt.**

- Điểm tích cực: HTML có dùng các vùng ngữ nghĩa như `header`, `nav`, `main`, `section`; CSS được tách riêng và có sử dụng biến, Flexbox và Grid.
- Cần sửa: tài liệu HTML bị lặp trong cùng file; có hai vùng `<main>`; phần liên hệ thiếu `<form>` và nhãn `<label>` gắn với trường nhập.
- Chưa có bộ kiểm thử tự động, quy tắc lint/format hoặc kiểm tra HTML/CSS trong quy trình dự án.

**Minh chứng:** Kiểm tra DOM trực tiếp ghi nhận `mainElements = 2`, `forms = 0`.

## 6. Khả năng triển khai

**Kết quả: Đạt một phần; chưa kiểm thử triển khai thực tế.**

- Cấu trúc phù hợp để phân phối như website tĩnh qua một web server hoặc dịch vụ hosting static; các đường dẫn tài nguyên trong trang là tương đối.
- Đã kiểm tra hiển thị bằng cách mở trang từ workspace cục bộ. Đây không phải kiểm thử trên hosting công khai.
- Chưa kiểm thử Docker, pipeline CI/CD, cấu hình tên miền/HTTPS, cache tài nguyên, trang lỗi máy chủ hoặc hành vi sau khi triển khai.
- README có hướng dẫn chạy web server cục bộ và lệnh Docker dùng Nginx; hướng dẫn không đồng nghĩa với việc các môi trường đó đã được xác nhận chạy thành công.

## Ảnh minh chứng

Đã chụp giao diện desktop, mobile và toàn trang trong phiên kiểm thử. Công cụ chụp của trình duyệt lưu ảnh vào vùng tài nguyên riêng của phiên, không vào workspace; tiện ích chụp màn hình macOS cũng không được cấp quyền truy cập màn hình trong phiên này. Vì vậy, hiện chưa có tệp ảnh trong `assets/css/docs/screenshots/` và không đính kèm liên kết giả. Cần chụp lại từ máy có quyền chụp màn hình và lưu ảnh vào thư mục trên trước khi nộp báo cáo.
