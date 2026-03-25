# IoTS Firmware Releases

Repository lưu trữ các phiên bản firmware cho board ESP32 của hệ thống **IoTS**.

---

## Cách upload firmware mới và deploy OTA

### Bước 1 — Build file .bin từ Arduino IDE / PlatformIO

- **Arduino IDE:** Sketch → Export Compiled Binary → lấy file `.bin` trong thư mục project
- **PlatformIO:** chạy `pio run` → lấy file trong `.pio/build/{board}/firmware.bin`

---

### Bước 2 — Tạo Release mới trên GitHub

1. Vào tab **Releases** → nhấn **"Create a new release"**
2. Nhấn **"Tag"** → gõ version mới (ví dụ `v1.0.1`) → chọn **"Create new tag"**
3. Nhập **Release title**: `Firmware v1.0.1`
4. Kéo thả file `.bin` vào vùng **"Attach binaries"** ở cuối trang
5. Nhấn **"Publish release"**

---

### Bước 3 — Lấy link download file .bin

Sau khi publish, trong mục **Assets**:

- Click chuột phải vào file `.bin` → **"Copy link address"**

Link có dạng:
```
https://github.com/{username}/{repo}/releases/download/v1.0.1/firmware.bin
```

---

### Bước 4 — Deploy OTA từ Web IoTS

1. Mở web IoTS → đăng nhập → chọn thiết bị
2. Vào tab **OTA Update**
3. Nhập **Phiên bản mới**: `1.0.1`
4. Nhập **URL file .bin**: dán link vừa copy ở Bước 3
5. Nhấn **Deploy**

Board ESP32 sẽ tự động:
- Nhận lệnh OTA từ Firebase
- Tải file `.bin` từ GitHub
- Ghi vào flash và khởi động lại

Trạng thái cập nhật hiển thị realtime trên web.

---

## Lưu ý

- Không tắt nguồn board trong quá trình OTA
- Mỗi lần update cần tạo **Release mới** với tag version mới
- Repo phải để **Public** để board tải được file

---

## Quy tắc đặt version firmware

| Thay đổi | Ví dụ |
|----------|-------|
| Sửa lỗi nhỏ | `1.0.0` → `1.0.1` |
| Thêm tính năng | `1.0.1` → `1.1.0` |
| Thay đổi lớn | `1.1.0` → `2.0.0` |

