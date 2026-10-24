# GoojodoQ FB051 — Bộ prompt tạo mặt đồng hồ tiếng Việt

Bộ prompt viết sẵn để tạo **ảnh nền mặt đồng hồ** cho **GoojodoQ Watch FB051** (mặt tròn 1,28 inch) bằng AI tạo ảnh, kèm trang kiểm tra ảnh và hướng dẫn đưa ảnh vào đồng hồ.

**Trang web:** https://khahdihdz.github.io/goojodoq-fb051-watchface-vi/

---

## Vấn đề của prompt thông thường

Hỏi AI "tạo mặt đồng hồ đẹp" thường nhận về một trong các kết quả sau:

| Kết quả | Vì sao không dùng được |
|---|---|
| Ảnh chụp một chiếc đồng hồ đeo tay | Đó là ảnh sản phẩm, không phải mặt đồng hồ |
| Mặt số có kim và số 12/3/6/9 | Kim vẽ trong ảnh sẽ lệch với giờ thật do máy hiển thị |
| Chữ sát bốn góc | Màn hình tròn cắt mất góc khi hiển thị |
| Chữ tiếng Việt sai dấu | AI tạo ảnh rất yếu với dấu tiếng Việt |
| Trung tâm sáng rực | Chữ giờ do ứng dụng vẽ đè lên sẽ chìm vào nền |

Bộ prompt trong repo này xử lý từng điểm trên bằng ràng buộc kỹ thuật cụ thể: khung 1:1, vùng an toàn đường kính 200 px, vùng giờ 140 × 72 px để trống, cấm kim và số giờ, ưu tiên nền tối.

---

## Dùng trong 4 bước

1. **Chọn prompt** — mở trang web, chọn *Prompt gốc* hoặc một trong 5 biến thể, bấm **Sao chép**.
2. **Tạo ảnh** — dán vào Gemini / ChatGPT / Midjourney / Flux. Điền `{{CHỦ_ĐỀ}}` và `{{BẢNG_MÀU}}` nếu dùng prompt gốc.
3. **Kiểm tra** — kéo ảnh vào mục *Kiểm tra ảnh* trên trang web để xem vòng an toàn và vùng giờ.
4. **Thu nhỏ và đưa vào máy** — resize về 240 × 240, rồi vào ứng dụng GoojodoQ → *Mặt đồng hồ* → *Tuỳ chỉnh / DIY* → chọn ảnh → lưu.

Hướng dẫn hậu kỳ chi tiết (ImageMagick, Python, prompt sửa ảnh): [`prompt/03-hau-ky.md`](prompt/03-hau-ky.md).

---

## Nội dung repo

```
.
├── index.html              Trang web: khung 240×240, bộ prompt, công cụ kiểm tra ảnh
├── prompt/
│   ├── 01-prompt-goc.md    Prompt khung xương + ý nghĩa từng biến
│   ├── 02-bien-the.md      5 biến thể: phố cổ, HUD, lịch Việt, thể thao, tối giản
│   └── 03-hau-ky.md        Thu nhỏ, kiểm tra, prompt sửa ảnh, lỗi thường gặp
├── docs/
│   └── thiet-bi.md         Thông số FB051, cách xác minh, giới hạn của máy
├── README.md
└── LICENSE
```

Trang web là một file HTML duy nhất, không phụ thuộc thư viện ngoài, chạy được cả khi mở trực tiếp bằng `file://`.

---

## Thông số đang dùng

| Hạng mục | Giá trị |
|---|---|
| Thiết bị | GoojodoQ FB051 |
| Kiểu màn hình | Tròn, 1,28 inch |
| Ảnh nền | 240 × 240 px (giả định — cần xác minh) |
| Vùng hiển thị | Hình tròn Ø 240 px |
| Vùng an toàn | Hình tròn Ø 200 px |
| Vùng giờ | 140 × 72 px, tâm lệch xuống 8 px |
| Định dạng | PNG/JPG, RGB, không alpha, dưới 60 KB |

> **Về độ phân giải:** trang bán hàng chỉ xác nhận 1,28 inch; một bài đánh giá ghi 240 × 240. Các mẫu cùng cỡ có thể dùng 240 × 280. Toàn bộ bố cục trong repo tính theo **tỉ lệ**, nên nếu máy thật khác, bạn chỉ cần đổi kích thước đầu ra chứ không phải thiết kế lại. Cách kiểm tra: [`docs/thiet-bi.md`](docs/thiet-bi.md).

---

## Vì sao phải chừa vùng giờ?

Ứng dụng của các mẫu đồng hồ giá rẻ thường chỉ nhận **ảnh nền**, sau đó tự vẽ giờ:phút lên trên bằng font hệ thống, ở vị trí cố định. Người dùng không điều khiển được vị trí, màu hay cỡ chữ đó.

Vì vậy:

- Trung tâm ảnh phải **tối và trống** — nếu không, giờ sẽ chìm.
- Không vẽ kim hay số giờ — chúng sẽ mâu thuẫn với giờ thật.
- Không đặt chữ quan trọng ở vành dưới nếu ứng dụng vẽ giờ ở đó.

Nếu ứng dụng của bạn cho phép chọn vị trí giờ, hãy dùng đúng vùng đó và bỏ ràng buộc "trung tâm trống" trong prompt.

---

## Giới hạn

- Đây là quy trình **ảnh nền**, không phải biên dịch firmware. FB051 không có định dạng mặt đồng hồ đóng gói công khai như đồng hồ Xiaomi/Amazfit.
- Không phải mọi lô FB051 dùng chung một ứng dụng. Tên mục "mặt đồng hồ tuỳ chỉnh" có thể khác nhau: *Tuỳ chỉnh*, *DIY*, *Album*, *Mặt đồng hồ ảnh*.
- Chưa có xác nhận chính thức từ nhà sản xuất về độ phân giải và vị trí vẽ giờ. Mọi thông số đều ghi rõ mức chắc chắn.
- Bộ prompt không tạo ra ảnh hoàn hảo ngay lần đầu. Kế hoạch thực tế: tạo 3–5 ảnh, chọn 1, sửa bằng prompt chỉnh ảnh.

---

## Chạy trang web cục bộ

```bash
cd goojodoq-fb051-watchface-vi
python3 -m http.server 8080
# mở http://localhost:8080
```

Hoặc mở thẳng `index.html` bằng trình duyệt — không cần máy chủ.

---

## Giấy phép

MIT. Prompt và nội dung hướng dẫn được tự do dùng, sửa, chia sẻ.
