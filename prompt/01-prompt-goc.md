# Prompt gốc — nền mặt đồng hồ GoojodoQ FB051

Đây là prompt "khung xương". Điền các biến `{{...}}` rồi dán nguyên khối vào ô nhập của công cụ tạo ảnh (Gemini, ChatGPT, Midjourney, Flux, Stable Diffusion…).

Nếu công cụ chỉ xuất được ảnh lớn (1024 × 1024), vẫn dùng prompt này — bố cục theo tỉ lệ là đúng — rồi thu nhỏ về 240 × 240 theo hướng dẫn ở [03-hau-ky.md](03-hau-ky.md).

---

## Khối prompt

```text
VAI TRÒ
Bạn là nhà thiết kế mặt đồng hồ số, chuyên tạo ảnh nền cho smartwatch màn hình tròn.

MỤC TIÊU
Tạo MỘT ảnh nền mặt đồng hồ, tỉ lệ 1:1, kích thước 240 × 240 pixel, dùng làm mặt đồng hồ tuỳ chỉnh cho GoojodoQ FB051 (màn hình tròn 1,28 inch, 240 × 240 px).

QUY TẮC KỸ THUẬT (bắt buộc)
1. Ảnh vuông chính xác 1:1. Không viền trắng, không khung, không vẽ thân đồng hồ, dây đeo, bóng đổ, không mô phỏng thiết bị, không watermark, không chữ ký tác giả.
2. Ảnh sẽ được ứng dụng cắt thành hình tròn đường kính 240 px. Mọi nội dung quan trọng phải nằm trong hình tròn đường kính 200 px, tức cách đều mép ảnh 20 px.
3. Chừa một vùng trống hình chữ nhật khoảng 140 × 72 px ở giữa ảnh (tâm vùng này lệch xuống 8 px so với tâm ảnh) để ứng dụng tự vẽ giờ:phút. Vùng này phải là nền sạch: không chữ, không số, không hoa văn nhỏ.
4. Không vẽ kim đồng hồ. Không vẽ vạch chia giờ. Không vẽ số 12, 3, 6, 9. Không vẽ giờ, ngày, tháng cụ thể.
5. Tương phản cao: nền tối, chi tiết sáng vừa phải. Không dùng mảng sáng lớn ở trung tâm vì sẽ làm chìm chữ giờ do ứng dụng vẽ lên.
6. Ưu tiên hình khối, gradient, hoa văn. Nếu có chữ: tối đa 6 từ, chiều cao chữ tối thiểu 14 px trên ảnh 240 px, tiếng Việt có dấu đầy đủ, không viết tắt, không trộn tiếng Anh.

CHỦ ĐỀ
{{CHỦ_ĐỀ}}

BỐ CỤC
- Vành trên (góc 10 giờ đến 2 giờ): điểm nhấn chính, có thể là một dòng chữ nhỏ hoặc một motif.
- Hai bên vành (3 giờ và 9 giờ): chi tiết phụ đối xứng hoặc bất đối xứng có chủ đích.
- Vành dưới (góc 5 giờ đến 7 giờ): một dòng chữ nhỏ hoặc một biểu tượng duy nhất.
- Trung tâm: để trống cho giờ:phút.
- Các chi tiết xuyên tâm hướng về tâm ảnh, không cắt ngang vùng trống ở giữa.

BẢNG MÀU
{{BẢNG_MÀU}}

PHONG CÁCH
Phẳng, sạch, sắc nét, không nhiễu hạt, không noise, không hiệu ứng 3D quá đà. Tối ưu để đọc trên màn hình 1,28 inch. Viền ngoài sẫm hơn nền 15–20% để hoà vào khung máy.

KHÔNG ĐƯỢC CÓ
- Chữ méo, chữ thiếu dấu, chữ vô nghĩa, chữ giả kiểu lorem ipsum.
- Hình mô phỏng đồng hồ, mặt số, kim, vạch chia.
- Logo thương hiệu thật (Apple, Samsung, Xiaomi, GoojodoQ…).
- Chi tiết mảnh dưới 2 px hoặc nội dung sắc nhọn, nhạy cảm.
- Khung viền giả lập màn hình.

ĐẦU RA
Một ảnh vuông 240 × 240 px. Không kèm lời giải thích, không chú thích ngoài ảnh.
```

---

## Ý nghĩa các biến

| Biến | Nội dung cần điền | Ví dụ |
|---|---|---|
| `{{CHỦ_ĐỀ}}` | Một câu mô tả ý tưởng, chất liệu, cảm xúc | "Đêm phố cổ Hà Nội, mái ngói cong và đèn lồng, tĩnh lặng, sang trọng" |
| `{{BẢNG_MÀU}}` | 4–6 mã màu kèm vai trò | "Nền #0C0A08; đèn lồng #E8A33D; tường vôi #C9B79C; nhấn #C2452F" |

## Ba câu bổ trợ nên thêm khi cần

- **Muốn ít chữ hơn:** `Chỉ dùng tối đa 2 từ tiếng Việt trong toàn ảnh.`
- **Muốn nền tối tuyệt đối:** `Nền đen #000000, chỉ dùng 2 màu nhấn, không gradient lan vào vùng giữa.`
- **Muốn đồng bộ khung máy:** `Viền ngoài cùng 12 px tối dần về #000000 để hoà với viền màn hình tròn.`

## Mẹo dùng theo công cụ

| Công cụ | Cách dùng |
|---|---|
| Gemini / ChatGPT (tạo ảnh) | Dán cả khối, thêm câu "xuất ảnh vuông" nếu cần |
| Midjourney | Thêm `--ar 1:1 --style raw`, bỏ phần "ĐẦU RA" |
| Flux / Stable Diffusion | Dùng khối trên làm prompt dương, sao chép mục "KHÔNG ĐƯỢC CÓ" sang prompt âm (negative) |

> Prompt càng cụ thể về **vị trí** thì ảnh càng dễ dùng. Nếu ảnh ra bố cục lệch, đừng viết lại từ đầu — dùng prompt sửa trong [03-hau-ky.md](03-hau-ky.md).
