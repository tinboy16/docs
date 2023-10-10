---
description: https://t.me/VNBnodegroup
---

# Cài Ubuntu Server lên VM WARE

tele nhóm: [https://t.me/VNBnodegroup](https://t.me/VNBnodegroup)

X nhóm : [https://x.com/vnbnode](https://x.com/vnbnode)

### 1. Ubuntu Server

**Ubuntu Server** là một hệ điều hành mã nguồn mở và miễn phí. Nếu bạn cần một máy chủ để triển khai các ứng dụng thì **Ubuntu Server** là một lựa chọn tốt.Mặc định **Ubuntu Server** sau khi cài đặt xong nó không có giao diện đồ họa người dùng. Và bạn cần phải sử dụng các lệnh (**Command Line**) để làm việc với nó.Sau khi cài đặt xong **Ubuntu Server**, bạn có tiếp 2 lựa chọn:Cài đặt Putty trên máy tính của bạn (Xem thêm tại phụ lục phía cuối tài liệu).**Putty** là một ứng dụng cho phép bạn kết nối từ xa với **Ubuntu Server**, và có thể thực thi các dòng lệnh **Command Line** trên **Putty** để tương tác với **Ubuntu Server**.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088850-vi.webp)

Cài đặt giao diện đồ họa cho Ubuntu Server.Như đã nói ở trên **Ubuntu Server** mặc định khi cài đặt xong không có giao diện đồ họa người dùng. Tuy nhiên bạn có thể cài đặt nó như một tùy chọn thêm. Và cài đặt **VNC Server** để bạn có thể điều khiển nó từ xa (Giống như việc bạn sử dụng chức năng **Remote** giữa các máy tính sử dụng hệ điều hành **Windows**).

### 2. Download Ubuntu 22.04

Để download **Ubuntu Server** bạn vào địa chỉ:

* [https://www.ubuntu.com/download/server](https://www.ubuntu.com/download/server)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Phiên bản mới nhất cho tới thời điểm này là **Ubuntu Server 22.04**, chúng ta sẽ download và cài đặt phiên bản này.

> Chú ý: Nếu bạn muốn tìm kiếm các phiên bản khác, hãy truy cập đường link dưới đây:
>
> * [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

Sau khi download bạn có được:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088889-vi.webp)

### 3. Cài đặt Ubuntu Server trên VmWare

Trong hướng dẫn này tôi cài đặt **Ubuntu Server** lên **VmWare** phiên bản 12.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088903-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088904-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088905-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088906-vi.webp)

Đặt tên cho máy ảo và chọn vị trí cài đặt.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088912-vi.webp)

Tiếp theo bạn cần chỉ định dung lượng ổ cứng cấp cho **Ubuntu**. Ở đây tôi đặt là **45GB**.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088918-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088919-vi.webp)

Bạn có thể hiệu chỉnh số lượng **RAM** cấp cho **Ubuntu Server**:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088925-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088926-vi.webp)

Trỏ tới vị trí file cài đặt **Ubuntu Server** mà bạn đã download trước đó.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088932-vi.webp)

Bắt đầu cài đặt:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088938-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088939-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088940-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088941-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088942-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088943-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088944-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088945-vi.webp)

**Ubuntu Server** đang được cài đặt:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088951-vi.webp)

Tiếp theo đặt **hostname** (tên máy tính) cho **Ubuntu Server**, chẳng hạn **abc.com** hoặc **myubuntu**,...

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088957-vi.webp)

Tạo một user, user này sẽ sử dụng để đăng nhập vào hệ điều hành **Ubuntu** sau khi cài đặt xong.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088963-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088964-vi.webp)

Nhập mật khẩu cho user.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088970-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088971-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088972-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088973-vi.webp)

Cấu hình phân vùng ổ cứng.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088979-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088980-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088981-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088982-vi.webp)

**Ubuntu Server** đang được cài đặt:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088988-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088989-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088990-vi.webp)

Tiếp theo có một vài tùy chọn bạn có thể cài đặt thêm, nó tùy thuộc vào muc đích sử dụng của bạn, chọn các phần mềm bạn muốn cài đặt thêm và nhấn Enter.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088996-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088997-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1088998-vi.webp)

Lúc này bạn đã cài đặt **Ubuntu Server** thành công.

### 4. Sử dụng Ubuntu Server

Sau khi cài đặt xong, hệ điều hành Ubuntu sẽ được khởi động:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089017-vi.webp)

Chú ý rằng **Ubuntu Server** không có giao diện người dùng, vì vậy bạn phải làm việc với nó thông qua các dòng lệnh (Command Line). Trước hết bạn cần đăng nhập vào hệ thống:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089023-vi.webp)

Đăng nhập thành công:

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089029-vi.webp)

Ví dụ bạn có thể nhập vào dòng lệnh sau để kiểm tra phiên bản của hệ điều hành.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089035-vi.webp)

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089036-vi.webp)

Hoặc sử dụng lệnh **"ifconfig"** để kiểm tra địa chỉ **IP** của Server.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089042-vi.webp)

### 5. Cài đặt PuTTY

**Putty** là một công cụ cho phép bạn kết nối từ xa vào **Ubuntu Server**, và gửi các lệnh tới **Ubuntu Server**.

![](https://s1.o7planning.com/web-rs/web-image/vi/arf-1089054-vi.webp)

tele nhóm: [https://t.me/VNBnodegroup](https://t.me/VNBnodegroup)
