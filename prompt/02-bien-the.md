# 5 biến thể dùng ngay

Mỗi biến thể đã điền sẵn `{{CHỦ_ĐỀ}}` và `{{BẢNG_MÀU}}`. Cách dùng: mở [01-prompt-goc.md](01-prompt-goc.md), thay hai biến bằng nội dung bên dưới, rồi dán cả khối vào công cụ tạo ảnh.

Bảng chọn nhanh:

| # | Tên | Cảm giác | Hợp với |
|---|---|---|---|
| 1 | Đêm phố cổ | Ấm, hoài niệm, sang | Dây da nâu, dây lưới vàng |
| 2 | HUD kỹ thuật | Lạnh, công nghệ | Dây silicon đen |
| 3 | Lịch Việt | Mộc, thủ công | Dây vải, dây da sáng |
| 4 | Thể thao | Nhanh, mạnh | Dây silicon cam/đen |
| 5 | Tối giản kim loại | Tối, thanh lịch | Dây thép, dây milanese |

---

## 1. Đêm phố cổ

```text
{{CHỦ_ĐỀ}} = Đêm phố cổ Hà Nội: mái ngói cong, đèn lồng giấy, mảng tường vôi loang, tĩnh lặng và sang trọng. Chi tiết tập trung ở vành trên và hai bên, trung tâm là mảng tối sạch.
{{BẢNG_MÀU}} = Nền #0C0A08; nền phụ #17110C; đèn lồng #E8A33D; tường vôi #C9B79C; mái ngói #5A3A2A; nhấn đỏ #C2452F.
```

Gợi ý thêm: `Mái ngói chỉ xuất hiện ở vành trên, uốn theo cung tròn, không chạm vùng giữa.`

---

## 2. HUD kỹ thuật

```text
{{CHỦ_ĐỀ}} = Giao diện HUD kỹ thuật tối giản: vòng cung mảnh, vạch chia áp suất, lưới toạ độ mờ, ánh cyan nhẹ. Cảm giác chính xác, lạnh, hiện đại.
{{BẢNG_MÀU}} = Nền #05080C; panel #0B1218; cyan #35E0D0; xanh lưới #123038; cảnh báo #FF7A45; chữ #D8F3EF.
```

Gợi ý thêm: `Vạch chia chỉ ở vành ngoài, dài 4–8 px, mật độ thưa, không tạo thành mặt số.`

---

## 3. Lịch Việt

```text
{{CHỦ_ĐỀ}} = Trang giấy dó Việt Nam: hoa sen chạm nổi mờ, đường tròn mảnh như triện mực, mảng mực tàu loang nhẹ ở góc. Mộc mạc, thủ công, yên tĩnh.
{{BẢNG_MÀU}} = Nền giấy #EDE3CE; mực #1C1A17; sơn mài đỏ #A8322A; lá sen #4F6B4A; vàng cũ #B08A3E.
```

Gợi ý thêm: `Nền sáng, nên mọi chi tiết phải nằm ngoài vùng giữa; chữ dùng màu mực #1C1A17.`

> Biến thể này là nền sáng. Nếu ứng dụng vẽ giờ bằng chữ trắng, hãy bỏ biến thể này hoặc kiểm tra lại màu chữ giờ trước khi dùng.

---

## 4. Thể thao

```text
{{CHỦ_ĐỀ}} = Mặt đồng hồ thể thao năng động: dải chéo chuyển động, vệt tốc độ, vòng cung nhịp tim cách điệu. Gọn, mạnh, dễ đọc khi đang chạy.
{{BẢNG_MÀU}} = Nền #0A0A0B; xám #2A2D31; cam #FF6B2C; trắng #F5F5F5; xám nhạt #6B7076.
```

Gợi ý thêm: `Dải chéo chỉ ở góc 4 giờ và 8 giờ, không cắt qua tâm.`

---

## 5. Tối giản kim loại

```text
{{CHỦ_ĐỀ}} = Mặt đồng hồ tối giản sang trọng: nền đen nhám, một vòng titan xước mảnh, vài đường khắc chìm, không hoa văn thừa. Cảm giác đắt tiền, im lặng.
{{BẢNG_MÀU}} = Nền #0E0F11; titan #B8BFC7; vàng đồng #C9A227; xám khói #3A3F45; chữ #E6E9EC.
```

Gợi ý thêm: `Chỉ một vòng titan duy nhất, dày 2 px, đường kính 196 px, không thêm vòng thứ hai.`

---

## Cách trộn biến thể

Muốn "chất Việt" nhưng vẫn hiện đại: lấy **bảng màu** của *Đêm phố cổ* + **bố cục** của *HUD kỹ thuật*. Ghi rõ trong prompt:

```text
Giữ bố cục vòng cung và lưới mờ kiểu HUD, nhưng dùng bảng màu đêm phố cổ (nền #0C0A08, nhấn #E8A33D).
```
