# Hậu kỳ: từ ảnh AI đến mặt đồng hồ dùng được

Mục tiêu: ảnh cuối cùng là **PNG 240 × 240**, đúng vùng an toàn, dung lượng nhỏ, không bị ứng dụng cắt mất chữ.

---

## 1. Kiểm tra ảnh trước khi thu nhỏ

Mở trang web của repo, kéo ảnh vào khung **Kiểm tra ảnh**. Trang sẽ:

- báo kích thước thật của ảnh;
- vẽ vòng an toàn đường kính 200 px;
- vẽ vùng giờ 140 × 72 px;
- tô mờ phần nằm ngoài hình tròn.

Nếu chữ hoặc chi tiết quan trọng rơi ra ngoài vòng an toàn, hãy sửa ảnh bằng prompt bên dưới thay vì cắt bớt.

---

## 2. Thu nhỏ về đúng 240 × 240

### Bằng ImageMagick (Termux, Linux, macOS)

```bash
magick input.png -resize 240x240^ -gravity center -extent 240x240 -strip -colors 128 PNG8:face.png
```

- `-resize 240x240^` phóng cho đầy khung, giữ tỉ lệ.
- `-gravity center -extent 240x240` cắt đều hai bên.
- `-strip` xoá metadata.
- `-colors 128 PNG8:` giảm dung lượng, an toàn cho mặt đồng hồ ảnh.

### Bằng Python (Pillow)

```python
from PIL import Image, ImageOps

img = Image.open("input.png").convert("RGB")
img = ImageOps.fit(img, (240, 240), method=Image.LANCZOS, centering=(0.5, 0.5))
img = img.quantize(colors=128, method=Image.MEDIANCUT, dither=Image.FLOYDSTEINBERG).convert("RGB")
img.save("face.png", optimize=True)
```

Kiểm tra kết quả:

```bash
file face.png        # phải ghi 240 x 240
du -h face.png       # nên dưới 60 KB
```

> Nếu máy không có ImageMagick, dùng Python ở trên. Nếu không có cả hai, dùng công cụ cắt ảnh online rồi tải về.

---

## 3. Prompt sửa ảnh (khi ảnh đầu chưa đạt)

Dán ảnh vào công cụ tạo ảnh, kèm một trong các câu sau:

**Chữ bị lệch tâm hoặc chạm mép**

```text
Giữ nguyên phong cách và bảng màu. Dịch toàn bộ nội dung vào trong: không chi tiết nào được nằm ngoài hình tròn đường kính 200 px tính trên khung 240 px. Vùng giữa 140 × 72 px phải trống hoàn toàn.
```

**Có kim hoặc số giờ**

```text
Xoá toàn bộ kim đồng hồ, vạch chia giờ và các số 12, 3, 6, 9. Chỉ giữ nền và hoa văn trang trí.
```

**Trung tâm quá sáng, chữ giờ sẽ bị chìm**

```text
Làm tối vùng trung tâm 140 × 72 px xuống còn khoảng 20% độ sáng hiện tại, giữ nguyên chi tiết ở vành ngoài.
```

**Chữ tiếng Việt sai dấu**

```text
Xoá toàn bộ chữ trong ảnh. Không thêm chữ mới. Chỉ giữ hình khối và hoa văn.
```

> Cách chắc ăn nhất với chữ tiếng Việt: **đừng để AI viết chữ**. Tạo nền không chữ, rồi thêm chữ bằng công cụ đồ hoạ (Canva, Figma, Photopea) với font có đủ dấu như Be Vietnam Pro, Lora, hoặc Noto Serif.

---

## 4. Checklist trước khi đưa vào đồng hồ

- [ ] Ảnh đúng 240 × 240 px, tỉ lệ 1:1.
- [ ] Không có chữ/chi tiết quan trọng ngoài đường tròn 200 px.
- [ ] Vùng giữa 140 × 72 px trống, tối, không hoa văn.
- [ ] Không có kim, vạch chia giờ, số 12/3/6/9.
- [ ] Không có watermark, logo thương hiệu khác.
- [ ] Chữ tiếng Việt đúng dấu (nếu có chữ).
- [ ] Dung lượng dưới 60 KB, định dạng PNG hoặc JPG.
- [ ] Đã xem thử trên khung tròn 240 px của trang web, không chỉ xem ảnh vuông.

---

## 5. Lỗi thường gặp

| Hiện tượng | Nguyên nhân | Cách xử lý |
|---|---|---|
| Chữ bị cắt hai bên | Ảnh vuông nhưng nội dung sát mép | Kéo nội dung vào trong 20 px, hoặc thu nhỏ ảnh 90% rồi thêm nền |
| Mặt đồng hồ bị mờ | Ảnh gốc nhỏ hơn 240 px | Tạo lại ở 1024 px rồi thu nhỏ, không phóng ảnh nhỏ |
| Giờ bị chìm | Vùng giữa quá sáng | Làm tối vùng giữa, hoặc chọn biến thể nền tối |
| Màu bị vỡ thành vệt | Giảm màu quá tay | Dùng `-colors 128` thay vì 64, hoặc giữ PNG 24-bit |
| Ứng dụng báo ảnh không hợp lệ | Ảnh có alpha hoặc quá lớn | Chuyển sang RGB, xoá alpha, nén dưới 200 KB |
