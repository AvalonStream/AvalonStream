# Avalon

### Một PC Windows 10/11 x64. Nhiều desktop độc lập.

Avalon biến một máy chủ Windows 10/11 x64 thành nhiều phiên bản desktop có thể truy cập độc lập. Mỗi instance có thể có phiên Windows, màn hình ảo, input, âm thanh, ứng dụng, trò chơi và kết nối Moonlight riêng.

**Một host. Nhiều instance.**

[English](README.md)

[Development log và phản hồi](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / lỗi và yêu cầu tính năng](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon là gì?

Avalon là nền tảng streaming desktop đa phiên dành cho Windows 10/11 x64. Thay vì dành toàn bộ PC cho một desktop tương tác duy nhất, Avalon cho phép nhiều instance Windows độc lập chạy song song trên cùng một host mà không cần một máy ảo đầy đủ cho mỗi người dùng.

---

## Khả năng chính

- Nhiều instance Windows độc lập trên một host
- Ngữ cảnh streaming riêng cho từng instance
- Màn hình ảo, độ phân giải và tần số quét theo từng instance
- Đường keyboard, mouse và audio phiên độc lập
- Avalon duy trì vòng đời phiên mà không cần giữ client RDP bên ngoài luôn kết nối
- Tạo, ghép cặp, xem trạng thái và chẩn đoán qua Web
- Moonlight vẫn là client trên điện thoại, tablet, TV và PC

---

## Cách hoạt động

Tạo một instance, chọn thiết lập hiển thị và ghép cặp client. Avalon chuẩn bị phiên Windows, màn hình ảo, ngữ cảnh streaming và vòng đời; sau đó bạn kết nối bằng Moonlight.

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Được thiết kế cho Moonlight

Avalon thay đổi phía host chứ không thay client quen thuộc. Moonlight vẫn có thể dùng trên Windows, Linux, macOS, Android, iOS/iPadOS, Android TV và các thiết bị được hỗ trợ khác.

---

## Tình huống sử dụng phổ biến

- Gaming tại nhà: nhiều người dùng các instance khác nhau cùng lúc
- Nhiều tài khoản và workload multi-instance
- Nhiều workstation từ xa trên một PC mạnh
- Kiểm thử, tự động hóa và môi trường tương thích
- Homelab và remote computing tự host

---

## Mô hình cách ly

Avalon cung cấp cách ly ở cấp phiên Windows, không phải cách ly máy ảo đầy đủ. Desktop, ứng dụng, màn hình, input và audio được tách theo instance, nhưng Windows host, kernel, CPU, GPU và phần cứng vật lý vẫn dùng chung. Không nên xem Avalon là ranh giới bảo mật tương đương VM.

---

## Nền tảng và hiệu năng

Avalon hướng tới Windows 10 và Windows 11 64-bit. Độ phân giải, tần số quét, codec, HDR và số instance đồng thời phụ thuộc GPU, driver, encoder, mạng và phần cứng client.

---

## Trạng thái dự án

Avalon hiện đang ở giai đoạn Alpha. Giao diện, khả năng tương thích và các thành phần mức thấp vẫn tiếp tục thay đổi, vì vậy có thể xuất hiện breaking changes và trường hợp biên theo phần cứng.

---

## Phát triển và phản hồi

README này là phần giới thiệu sản phẩm ổn định. Cập nhật phát triển theo thời gian thực và hướng dẫn gửi phản hồi được duy trì riêng trong development log.

- [Development log và phản hồi](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / lỗi và yêu cầu tính năng](https://github.com/AvalonStream/AvalonStream/issues)

**Một host. Nhiều instance.**
