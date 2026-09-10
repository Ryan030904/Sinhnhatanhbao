# KẾ HOẠCH PHÁT TRIỂN: TROLL ANH BẢO (NÚT NÉ & ÉP CHỮ) 🤪

Tài liệu thiết kế chi tiết tính năng troll Anh Bảo tích hợp từ nút "Bất ngờ" trong web sinh nhật.

---

## 1. Mục Tiêu Chính

- **Điểm bắt đầu**: 
  - Thêm 1 nút bấm mang tên **"Bất ngờ"** nằm ở thanh công cụ dưới, ngay cạnh nút *"Thổi Nến" / "Thắp Lại Nến"*.
  - Khi người xem bấm vào nút **"Bất ngờ"**, sẽ chuyển ngay vào trang câu hỏi troll.

- **Hình nền trang troll**:
  - Sử dụng tệp ảnh: `1788408786081_6636310689048689903_g5796357033961494663_ab93c8728127a2521311887a9ad4ea22.jpg` (ảnh Anh Bảo nằm trong lồng xông hơi cực hài hước).
  - Có lớp phủ làm mờ / tối nhẹ nhàng (overlay) để chữ và giao diện nổi bật, dễ đọc.

- **Mục tiêu 1: Màn hình câu hỏi & Nút "Không" né tránh**:
  - **Vị trí khung câu hỏi**: Nằm cao lên ở nửa trên màn hình, thiết kế gọn gàng để lộ rõ khuôn mặt và biểu cảm hài hước của Anh Bảo ở nền phía dưới.
  - **Nội dung câu hỏi**: *"Anh bảo có hay bù khu mấy ông già ko!?=))"*
  - **Nút "Có"**: Bấm vào sẽ chuyển ngay sang bước Khung Nhập Bị Ép Chữ.
  - **Nút "Không"**: Chuột hoặc ngón tay chạm lại gần sẽ tự động nhảy né sang vị trí ngẫu nhiên khác **trong khuôn khổ màn hình thấy được** (không bị nhảy ra ngoài hay biến mất), và **luôn giữ nguyên chữ "Không"** chứ không được đổi thành từ khác ("Đố...").

- **Mục tiêu 2: Khung nhập bị ép chữ (Forced Typing)**:
  - Dù Anh Bảo gõ bất kỳ phím gì trên bàn phím máy tính hoặc điện thoại, từng ký tự hiển thị ra khung chat sẽ bị ép theo đúng câu:
    👉 **`có, em giữ bí mật hộ nha 🥺`**
  - Chặn dán (paste), cắt (cut), kéo thả (drop) để đảm bảo trải nghiệm troll chuẩn xác.

- **Mục tiêu 3: Màn hình kết quả sau khi ấn Gửi**:
  - Sau khi gõ hết câu ép chữ, nút **"Gửi Đi Nè 💌"** sáng lên.
  - Khi ấn **"Gửi Đi Nè 💌"**, hiển thị ra bảng kết quả tương tự mẫu với nội dung:
    - Tiêu đề: **Ok anh bảo! Em biết chuyện đó lâu rồi, không có gì phải giấu cả :))**
    - Nội dung: **Đừng lo, em kín miệng lắm. Còn nga, nhi, chị linh thì em ko biết nha 😎😎**
    - Nút bấm: **`ahihi><`**
  - Khi ấn nút **`ahihi><`**: Tự động quay trở lại màn hình chọn "Có / Không" ban đầu, reset nút "Không" về vị trí cũ để tiếp tục troll.

---

## 2. Luồng Hoạt Động Chi Tiết (User Flow)

```
[Trang Bánh Sinh Nhật 3D]
       │
       ▼ (Bấm nút "Bất ngờ" ở thanh công cụ cạnh nút Thổi Nến)
[Trang Troll: Khung nằm cao gọn gàng, background ảnh xông hơi]
       │
       ▼
[Màn Hình Câu Hỏi: "Anh bảo có hay bù khu mấy ông già ko!?=))"]
  ├── Nút "Có" ───────► (Chuyển sang Khung Ép Chữ)
  └── Nút "Không" ────► Rê chuột/chạm: Tự né tránh trong khuôn khổ màn hình (luôn giữ chữ "Không")
       │
       ▼
[Khung Nhập Bị Ép Chữ]
  └── Gõ bất kỳ ký tự nào ──► Tự động gõ ra: "có, em giữ bí mật hộ nha 🥺"
       │
       ▼ (Gõ xong toàn bộ câu -> Nút "Gửi Đi Nè 💌" mở khóa)
[Bảng Kết Quả Troll]
  ├── Tiêu đề: "Ok anh bảo! Em biết chuyện đó lâu rồi, không có gì phải giấu cả :))"
  ├── Mô tả: "Đừng lo, em kín miệng lắm. Còn nga, nhi, chị linh thì em ko biết nha 😎😎"
  └── Nút "ahihi><" ──► Bấm vào quay lại màn hình câu hỏi Có / Không
```

---

## 3. Danh Sách Tệp Triển Khai

| Tệp | Trạng thái | Nhiệm vụ |
| :--- | :--- | :--- |
| `troll.html` | Tạo mới | Trang troll độc lập với nền ảnh Anh Bảo, xử lý né nút, ép chữ và bảng kết quả |
| `index.html` | Cập nhật | Bổ sung nút "Bất ngờ" cạnh nút thổi nến, điều hướng sang `troll.html` |
| `cake.html` | Cập nhật | Bổ sung nút "Bất ngờ" cạnh nút thổi nến |
