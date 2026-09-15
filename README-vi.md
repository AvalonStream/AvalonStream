<div align="center">

# Avalon

### Một PC Windows 10/11 x64. Nhiều desktop độc lập.

Biến một máy Windows 10/11 x64 thành nhiều instance desktop có thể truy cập độc lập, mỗi instance có màn hình, đầu vào, âm thanh, ứng dụng và kết nối streaming từ xa riêng.

**Một host. Nhiều instance.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Avalon là gì?

Avalon là nền tảng streaming desktop đa phiên dành cho Windows 10/11 x64.

Thay vì giới hạn một PC vào một desktop tương tác duy nhất, Avalon cho phép cùng một máy chạy đồng thời nhiều instance Windows độc lập.

Mỗi instance có thể có riêng:

- phiên desktop Windows
- màn hình ảo
- độ phân giải và tần số quét
- luồng đầu vào
- luồng âm thanh
- ứng dụng và trò chơi
- kết nối từ xa qua Moonlight

Nhờ vậy, một PC mạnh có thể hoạt động giống nhiều máy tính có thể truy cập từ xa mà không cần chạy một máy ảo đầy đủ cho từng người dùng.

---

## Thực tế trông như thế nào?

Hãy hình dung một PC Windows 10/11 x64 chạy ba instance Avalon:

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Mỗi client kết nối vào desktop Windows riêng của mình.

Các instance chạy song song mà không dùng chung desktop, con trỏ chuột, đầu ra âm thanh hay phiên ứng dụng.

---

## Vì sao chọn Avalon?

Các công cụ remote desktop truyền thống thường được thiết kế quanh mô hình một người dùng điều khiển một desktop.

Máy ảo mang lại khả năng cách ly mạnh, nhưng cũng kéo theo hệ điều hành bổ sung, chi phí bộ nhớ và lưu trữ, độ phức tạp GPU và công việc quản trị cao hơn.

Avalon chọn một hướng khác.

Nó kết hợp các phiên Windows, màn hình ảo, tiến trình streaming độc lập và quản lý vòng đời tập trung để nhiều desktop tương tác có thể cùng tồn tại trên một host Windows 10/11 x64.

Phần phức tạp được giữ bên trong Avalon. Với người dùng, quy trình rất đơn giản:

```text
Tạo instance
        ↓
Thiết lập màn hình và ghép nối
        ↓
Mở Moonlight
        ↓
Kết nối
```

---

## Khả năng cốt lõi

### Nhiều instance độc lập

Chạy nhiều phiên desktop Windows cùng lúc trên một host.

Mỗi instance hoạt động như một môi trường desktop tương tác riêng biệt.

### Streaming độc lập

Mỗi instance có ngữ cảnh streaming riêng và có thể được kết nối độc lập từ một client Moonlight.

Một TV có thể kết nối với một instance trong khi máy tính bảng hoặc PC khác đồng thời kết nối với instance khác.

### Màn hình độc lập

Mỗi instance có thể dùng cấu hình màn hình ảo riêng, bao gồm độ phân giải và tần số quét.

Avalon quản lý môi trường hiển thị mà không cần màn hình vật lý cho từng instance.

### Đầu vào độc lập

Bàn phím và chuột được định tuyến đến đúng phiên Windows thay vì được chia sẻ giữa tất cả instance.

Khi stack đầu vào tiếp tục phát triển, Avalon được thiết kế hướng đến cách ly thiết bị theo từng instance đầy đủ hơn.

### Âm thanh độc lập

Mỗi instance sử dụng đường âm thanh riêng của phiên Windows, vì vậy các người dùng khác nhau có thể nghe ứng dụng hoặc trò chơi khác nhau mà âm thanh không bị trộn đơn giản giữa các instance.

### Quản lý vòng đời phiên

Avalon tự tạo và duy trì các phiên.

Không cần giữ một client RDP bên ngoài kết nối liên tục chỉ để instance tiếp tục tồn tại.

### Quản lý qua Web

Tất cả instance được quản lý từ một giao diện Web duy nhất.

Các thao tác điển hình gồm:

- tạo và xóa instance
- khởi động và dừng instance
- thiết lập độ phân giải và tần số quét
- ghép nối client Moonlight
- kiểm tra trạng thái kết nối
- xem thông tin chẩn đoán
- quản lý thiết lập cấp host

Việc sử dụng hằng ngày không yêu cầu dòng lệnh.

---

## Được thiết kế cho Moonlight

Avalon giữ nguyên trải nghiệm streaming Moonlight quen thuộc.

Bạn vẫn có thể dùng Moonlight trên các thiết bị như:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TV và thiết bị streaming được Moonlight hỗ trợ

Avalon thay đổi cách tổ chức phía host, không bắt người dùng học một client streaming hoàn toàn mới.

---

## Trường hợp sử dụng

### Chơi game trong gia đình

Biến một PC gaming thành nhiều môi trường game độc lập cho nhiều người trong cùng gia đình.

Một người có thể chơi trên TV phòng khách trong khi người khác kết nối tới instance khác từ handheld hoặc laptop.

### Nhiều tài khoản và nhiều instance

Chạy các ứng dụng, tài khoản hoặc phiên game khác nhau trong các môi trường Windows tách biệt trên cùng một máy.

### Workstation từ xa

Dùng một desktop mạnh như nhiều không gian làm việc từ xa có thể truy cập độc lập.

### Kiểm thử và phát triển

Duy trì nhiều phiên Windows để kiểm thử phần mềm, tự động hóa, xác minh tương thích hoặc tạo môi trường người dùng cách ly.

### Homelab và self-hosting

Dùng một máy Windows hiệu năng cao làm host điện toán từ xa nhiều người dùng được quản lý tập trung.

---

## Avalon hoạt động như thế nào?

Avalon điều phối nhiều lớp hệ thống ở bên trong:

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

Người dùng thông thường không cần hiểu các chi tiết triển khai này.

Bạn tạo một instance; Avalon chuẩn bị phiên, màn hình, môi trường streaming và vòng đời; sau đó bạn kết nối.

---

## Mô hình cách ly

Avalon cung cấp **cách ly ở cấp phiên Windows**.

Mỗi instance có phiên Windows, desktop, ứng dụng, màn hình, đường đầu vào và đường âm thanh riêng.

Tuy nhiên, các instance Avalon **không phải máy ảo đầy đủ**.

Chúng vẫn dùng chung:

- cùng một cài đặt Windows trên host
- cùng kernel
- cùng CPU vật lý
- cùng GPU vật lý
- cùng tài nguyên phần cứng của host

Vì vậy không nên xem Avalon như một ranh giới bảo mật tương đương VM.

Mục tiêu là streaming nhiều người dùng và nhiều desktop hiệu quả, không phải ảo hóa phần cứng hoàn toàn.

---

## Trạng thái hiện tại

Avalon hiện đang ở giai đoạn **Alpha**.

Kiến trúc, giao diện quản lý, lớp tương thích và stack thiết bị vẫn đang tiếp tục phát triển.

Ở giai đoạn này có thể gặp:

- thay đổi không tương thích
- tương thích phần cứng chưa hoàn thiện
- thay đổi giao diện
- trường hợp biên liên quan đến driver và phiên
- hành vi tính năng có thể còn thay đổi trước bản ổn định

Avalon hiện chưa phù hợp để được coi là hạ tầng sản xuất quan trọng.

Kiểm thử, log, báo cáo lỗi có thể tái hiện và phản hồi từ sử dụng thực tế đặc biệt có giá trị ở giai đoạn này.

---

## Nền tảng

Mục tiêu hiện tại:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon được thiết kế cụ thể dựa trên mô hình desktop, phiên và đồ họa của Windows.

Hỗ trợ các hệ điều hành host khác hiện không phải mục tiêu chính của dự án.

---

## Hiệu năng

Hiệu năng streaming thực tế phụ thuộc vào nhiều yếu tố, bao gồm:

- GPU
- hỗ trợ encoder
- driver đồ họa
- độ phân giải
- tần số quét
- codec
- chất lượng mạng
- khả năng giải mã của client
- số lượng instance chạy đồng thời

Avalon không đảm bảo một độ phân giải, tần số quét, chế độ HDR hoặc số lượng instance đồng thời cố định trên mọi hệ thống.

Tài liệu tương thích sẽ được mở rộng khi phạm vi kiểm thử tăng lên.

---

## Triết lý dự án

Avalon được xây dựng quanh một ý tưởng đơn giản:

> Một PC mạnh không nên luôn bị giới hạn vào một màn hình, một desktop và một người dùng.

Host có thể chỉ là một máy. Trải nghiệm chạy trên đó không nhất thiết chỉ có một.

---

## Phát triển

README này được duy trì như phần giới thiệu sản phẩm Avalon ổn định.

Để xem tiến độ phát triển theo thời gian thực và thông báo dự án, hãy xem [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Để báo lỗi, đặt câu hỏi hoặc đề xuất tính năng, hãy dùng [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Một host. Nhiều instance.**

</div>
