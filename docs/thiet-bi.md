# Thiết bị: GoojodoQ FB051

## Thông số đang dùng trong bộ prompt

| Hạng mục | Giá trị | Mức chắc chắn |
|---|---|---|
| Mẫu máy | GoojodoQ Watch FB051 | Chắc chắn |
| Kiểu dáng | Mặt tròn | Chắc chắn |
| Đường chéo màn hình | 1,28 inch | Chắc chắn (trang bán hàng Lazada) |
| Độ phân giải | 240 × 240 px | **Giả định** — cần xác minh trên máy thật |
| Tỉ lệ ảnh nền | 1:1, cắt hình tròn | Suy ra từ kiểu dáng mặt tròn |
| Chống nước | IP67 | Theo nhà bán lẻ |
| Ứng dụng đồng bộ | Ứng dụng GoojodoQ / Da Fit (tuỳ lô hàng) | Cần kiểm tra trong hộp |

## Vì sao lại là 240 × 240?

- Màn hình tròn 1,28 inch không có độ phân giải phổ quát duy nhất. Các mẫu cùng cỡ thường dùng 240 × 240 hoặc 240 × 280.
- Một bài đánh giá FB051 trên Facebook ghi "màn hình tròn 1,28 inch, độ phân giải 240 × 240".
- Trang bán hàng chỉ xác nhận 1,28 inch, không ghi độ phân giải.

Vì vậy repo chọn 240 × 240 làm mốc thiết kế, và toàn bộ bố cục được làm **co giãn được** (vùng an toàn tính theo % chứ không theo pixel tuyệt đối) để dùng lại nếu máy thật là 240 × 280.

## Cách xác minh trên máy thật (2 phút)

1. Trên đồng hồ: `Cài đặt` → `Giới thiệu` / `Thông tin` → tìm dòng độ phân giải.
2. Hoặc trong ứng dụng điện thoại: mục `Thiết bị` → `Thông tin thiết bị`.
3. Hoặc thử nghiệm: đưa một ảnh 240 × 240 vào làm mặt đồng hồ. Nếu ảnh bị kéo giãn theo chiều dọc, máy dùng tỉ lệ khác 1:1 (khả năng cao 240 × 280).

Sau khi xác minh, cập nhật số liệu tại đây và trong `README.md`.

## Ứng dụng và mặt đồng hồ tuỳ chỉnh

Không phải mọi lô FB051 đều đi kèm cùng một ứng dụng. Trình tự chung:

1. Cài ứng dụng theo mã QR trong hộp hoặc trong `Cài đặt` → `Mã QR`.
2. Ghép đôi Bluetooth (có thể cần cả Bluetooth Classic cho cuộc gọi và BLE cho dữ liệu).
3. Vào `Mặt đồng hồ` → `Tuỳ chỉnh` / `DIY` / `Album` / `Mặt đồng hồ ảnh`.
4. Chọn ảnh từ thư viện (ảnh đã chuẩn bị 240 × 240), căn khung, lưu.

Nếu ứng dụng **không** có mục mặt đồng hồ tuỳ chỉnh:

- Kiểm tra cập nhật ứng dụng trước.
- Một số bản chỉ cho chọn ảnh khi đồng hồ đang kết nối và ở màn hình chính.
- Nếu vẫn không có, bộ prompt này vẫn dùng được để tạo ảnh nền cho mục `Ảnh nền` / `Watch face gallery` nếu máy hỗ trợ.

## Giới hạn cần biết

- Ứng dụng thường **tự vẽ giờ:phút** đè lên ảnh nền, vị trí và màu chữ do ứng dụng quyết định. Đó là lý do prompt yêu cầu chừa vùng giữa trống và giữ nền tối.
- Một số ứng dụng nén ảnh rất mạnh (64–128 màu). Chi tiết gradient mịn có thể bị vỡ thành vệt.
- Ảnh có vùng trong suốt (alpha) thường bị từ chối hoặc hiển thị nền đen.
- Không có chuẩn chung cho mặt đồng hồ FB051: không thể đóng gói `.bin` như đồng hồ Xiaomi/Amazfit. Đây là quy trình **ảnh nền**, không phải biên dịch firmware.

## Nguồn tham khảo

- Trang bán hàng Lazada: mô tả "Màn hình 1.28 inch" cho FB051.
- Bài đánh giá FB051 (Facebook): ghi "màn hình tròn 1,28 inch, độ phân giải 240 × 240".
- Trang hướng dẫn chính thức GoojodoQ: quy trình ghép đôi và thay mặt đồng hồ.

> Các nguồn trên là thông tin công khai, có thể thay đổi theo lô hàng. Luôn đối chiếu với máy thật trước khi thiết kế hàng loạt.
