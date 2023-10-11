# Guide systemd (Vietnamese)

Trước khi khởi động bạn phải có private key, có thể dùng limino wallet để tạo và stake 700erb vào chính ví của mình.

Nếu chưa có erb thì điền form\
https://global.erbie.io/FAQFeedback _(tìm đến dòng **validator apply** và điền)_

_Port sử dụng: 8544, 30303_

1. **Chạy lệnh tự động:**

```
wget -O erbie.sh https://raw.githubusercontent.com/johnt9x/erbie/main/erbie.sh && chmod +x erbie.sh && ./erbie.sh
```

2. **Sau khi chạy xong. Kiểm tra node bằng lệnh này**

```
wget -O monitor.sh https://raw.githubusercontent.com/johnt9x/erbie/main/monitor.sh && chmod +x monitor.sh && ./monitor.sh
```

Nếu hiện lên được số node connections và blockheight là được.



3. **Sau đó đổi private key theo ví mà bạn đã stake 700 erbie. **_**(không điền 0x)**_

```
sudo nano .erbie/erbie/nodekey
```

_Ctrl+k để xóa key cũ =>> dán key mới vào =>> ctrl+x và y để lưu lại._

4. **Dừng và khởi động lại erbie.**

```
systemctl stop erbied 
sudo systemctl restart erbied  
```

5. **Kiểm tra private key xem đúng không.**

```
cat .erbie/erbie/nodekey
```

Sau đó kiểm tra bằng lệnh monitor ở trên và chờ team stake 69300erb để lên validator thôi. Chúc các bạn thành công.

6. **Kiểm tra log.**

```
journalctl -fu erbied -o cat
```

7. **Các lệnh xóa node.**

```
systemctl stop erbied
systemctl disable erbied
rm -rf root/usr/local/bin/erbie
rm -rf erbie
rm -rf erbie.sh
rm -rf monitor.sh
rm -rf .erbie
```

8. **Cập nhật phiên bản mới.**

```
sudo systemctl stop erbied
cd && rm -rf erbie
git clone https://github.com/erbieio/erbie
cd erbie
git checkout v0.15.0
go build -o erbie cmd/erbie/main.go
mv erbie /usr/local/bin
sudo systemctl restart erbied
journalctl -fu erbied -o cat
```

Visit our communities:

Telegram group chat: [https://VNBnodechat](https://t.me/+4aLsnP6JHhY4YTY1)

Telegram news channel: [https://VNBnode\_news](https://t.me/+IpfWe\_pX7UlkMzY1)

Web: [https://VNBnode.com](https://vnbnode.com)&#x20;
