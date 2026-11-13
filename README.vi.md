# Chụp màn hình Deepin – bản phím tắt kiểu Lightshot, giao diện tiếng Việt

Bản sửa đổi của [deepin-screen-recorder](https://github.com/linuxdeepin/deepin-screen-recorder) 6.6.39
(app chụp và ghi màn hình mặc định của Deepin 25), thêm phím tắt giống Lightshot và giao diện tiếng Việt đầy đủ.

## Thay đổi so với bản gốc

### Phím tắt kiểu Lightshot (khi đang chọn vùng chụp)

| Phím | Tác dụng |
|---|---|
| **Ctrl+C** | Chép ảnh vào bảng tạm rồi đóng |
| **Ctrl+S** | Lưu ảnh như nút Lưu (bản gốc: chỉ chép vào bảng tạm) |
| **Ctrl+D** | Tải ảnh lên [catbox.moe](https://catbox.moe), chép link chia sẻ vào bảng tạm |
| **Ctrl+P** | In ảnh |
| **Ctrl+G** | Tìm ảnh tương tự bằng Google Lens |

App thoát ngay sau khi chụp, nên Ctrl+D/P/G lưu ảnh ra file tạm rồi giao cho chương trình phụ
[`src/share/dsr-share`](src/share/dsr-share) (Python, PyQt5) chạy độc lập. Chương trình được cài vào
`/usr/libexec/deepin-screen-recorder/dsr-share`.

### Giao diện tiếng Việt

- Bật bản dịch tiếng Việt (có sẵn trong mã nguồn nhưng bị thiếu trong `translations.pri`).
- Dịch đủ 177 câu, kể cả chú thích khi trỏ chuột vào các nút (Lưu vào máy, Lưu vào Màn hình nền,
  Chép vào bảng tạm (Enter), Công cụ hình học…), sửa các câu dịch sai.
- Rút gọn tên trong bảng cài đặt nhanh trên Dock (Chụp ảnh, Ghi hình) để không bị cắt chữ.

Các file đã sửa: `src/main_window.cpp`, `src/main_window.h`, `src/src.pro`, `src/share/dsr-share`,
`translations.pri`, `translations/deepin-screen-recorder_vi.ts`, `debian/control`, `debian/changelog`.

## Build và cài đặt (Deepin 25)

```bash
sudo apt build-dep .          # hoặc cài các gói trong Build-Depends của debian/control
dpkg-buildpackage -b -us -uc -j$(nproc)
sudo apt install ../deepin-screen-recorder_6.6.39+lightshot4_amd64.deb
```

Gói cần thêm `python3`, `python3-pyqt5`, `libnotify-bin`, `xdg-utils` (đã khai báo trong `debian/control`,
`apt install` tự cài).

## Giấy phép

GPL-3.0-or-later, giống bản gốc của Deepin (xem [LICENSE](LICENSE)). Bản quyền phần gốc thuộc UnionTech Software Technology Co., Ltd.
