# Lập trình Socket trong Java

Bài thực hành xây dựng ứng dụng Client-Server với Socket trong Java, minh họa 3 mô hình giao tiếp mạng: **TCP**, **UDP**, và **Multicast**.

Tham khảo: [gpcoder.com - Xây dựng ứng dụng Client-Server với Socket trong Java](https://gpcoder.com/3679-xay-dung-ung-dung-client-server-voi-socket-trong-java/)

## 1. TCP (Transmission Control Protocol)

Giao tiếp **có nối kết**, đảm bảo dữ liệu đến đúng thứ tự và không bị mất. Mô hình 1-1 giữa Client và Server.

- `1_EchoChatSingleServer`: Server phục vụ **tuần tự** — tại một thời điểm chỉ xử lý 1 Client.
- `2_EchoChatMultiServer`: Server phục vụ **song song** bằng multi-thread (`WorkerThread`) — xử lý nhiều Client cùng lúc.

📁 Code: `src/com/gpcoder/tcp/`
📸 Ảnh minh chứng: `screenshot/tcp/`

## 2. UDP (User Datagram Protocol)

Giao tiếp **không nối kết**, không đảm bảo thứ tự hay việc gói tin đến nơi, đổi lại tốc độ nhanh hơn TCP. Mô hình 1-1 (unicast), dùng `DatagramSocket` và `DatagramPacket`.

📁 Code: `src/com/gpcoder/udp/`
📸 Ảnh minh chứng: `screenshot/udp/`

## 3. Multicast

Mở rộng từ UDP, cho phép **1 Sender gửi - nhiều Receiver cùng nhận** một nội dung, cùng lúc. Receiver phải `joinGroup()` vào địa chỉ IP lớp D (`224.0.0.0` - `239.255.255.255`) để nhận được dữ liệu.

📁 Code: `src/com/gpcoder/multicast/`
📸 Ảnh minh chứng: `screenshot/multicast/`

## So sánh 3 mô hình

| Mô hình | Số người nhận | Đảm bảo tin cậy? | Ví dụ thực tế |
|---|---|---|---|
| TCP | 1-1 (unicast) | Có | Tải file, chat 1-1 |
| UDP | 1-1 (unicast) | Không | Voice chat đơn giản |
| Multicast | 1-nhiều | Không | Game nhiều người chơi, live streaming, routing protocol |
