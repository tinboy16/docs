# Hưỡng Dẫn dự án massa

**1.Cập nhật & Nâng cấp Máy chủ**

Trước khi bạn bắt đầu, cần **cập nhật** và **nâng cấp** máy chủ

```
sudo apt update && apt upgrade -yCopy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-2.png" alt="" height="179" width="679"><figcaption></figcaption></figure>

**2. Cài đặt điều kiện tiên quyết**

Sao chép và dán lệnh bên dưới khi thiết bị đầu cuối yêu cầu bạn, nhập **Y** và nhấn **ENTER** trên bàn phím của bạn.

```
sudo apt install pkg-config curl git build-essential libssl-dev libclang-dev ufw screenCopy
```

**3.Cài đặt Rust**

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | shCopy
```

Khi dấu nhắc lệnh yêu cầu nhập **1** và nhấn **ENTER** trên bàn phím của bạn.

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-3.png" alt="" height="274" width="666"><figcaption></figcaption></figure>

Định cấu hình đường dẫn:

```
source $HOME/.cargo/envCopy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-4.png" alt="" height="167" width="674"><figcaption></figcaption></figure>

Kiểm tra phiên bản Rust

```
rustc --versionCopy
```

**4. Cài đặt hàng đêm**

```
rustup toolchain install nightly-2023-01-30Copy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-5.png" alt="" height="149" width="678"><figcaption></figcaption></figure>

Đặt nó làm mặc định:

```
rustup default nightly-2023-01-30Copy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-6.png" alt="" height="84" width="676"><figcaption></figcaption></figure>

Kiểm tra phiên bản rỉ sét:

```
rustc --versionCopy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-7.png" alt="" height="65" width="683"><figcaption></figcaption></figure>

### Part04: Cài đặt và chạy Node <a href="#6c76" id="6c76"></a>

**1.Tải xuống nút**

```
git clone --branch testnet https://github.com/massalabs/massa.gitCopy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-8.png" alt="" height="68" width="683"><figcaption></figcaption></figure>

**2.Khởi động nút**

Mở một phiên màn hình mới để chạy massa node.

```
screen -S massaCopy
```

<figure><img src="https://validatorstress.fun/wp-content/uploads/2023/07/image-9.png" alt="" height="354" width="671"><figcaption></figcaption></figure>

Di chuyển đến thư mục liên quan:

```
cd massa/massa-node/Copy
```

Khởi chạy nút, trên Ubuntu:

```
RUST_BACKTRACE=full cargo run --release -- -p <PASSWORD> |& tee logs.txtCopy
```

Thay thế \<PASSWORD> bằng mật khẩu mà bạn sẽ cần giữ để khởi động lại nút của mình.

```
#Example

RUST_BACKTRACE=full cargo run --release -- -p Seengo |& tee logs.txtCopy
```

Chờ để kết thúc, khi dấu nhắc lệnh hiển thị cho bạn hình ảnh thích bên dưới sau đó nhấn **Ctrl + A** và **D** để tách phiên màn hình. Nút massa đang trong quá trình biên dịch. Có thể mất khoảng 15 phút.

**3.Khởi động máy khách**

Mở phiên màn hình thứ hai để chạy máy khách massa node.

```
screen -S massa-clientCopy
```

Di chuyển đến thư mục liên quan:

```
cd massa/massa-client/Copy
```

Ăn trưa cho khách hàng:

```
cargo run --release -- -p <PASSWORD>Copy
```

Thay thế \<PASSWORD> bằng mật khẩu mà bạn sẽ cần giữ để khởi động lại máy khách của mình Vui lòng đợi cho đến khi các thư mục được xây dựng trước khi chuyển sang bước tiếp theo.

```
#Example

cargo run --release -- -p SeengoClientCopy
```

Chờ kết thúc và đi đến bước tiếp theo.

### Part05: Ví <a href="#bc89" id="bc89"></a>

Nếu khách hàng của bạn đang chạy: Bây giờ bạn có thể tạo một cặp khóa mới (và địa chỉ được liên kết). Lưu thông tin ví của bạn trong tệp notepad và giữ chúng an toàn.

**1.Tạo Ví**

```
wallet_generate_secret_keyCopy
```

**2. chìa khóa**

Truy cập (các) khóa công khai của (các) địa chỉ:

```
wallet_get_public_key <Address1>Copy
```

```
#Example

wallet_get_public_key A12uRDBsRb2vDqm1XxjuhR1VGxxxxxxxxxxxxxxxxCopy
```

Truy cập (các) khóa bí mật của (các) địa chỉ:

```
wallet_get_secret_key <Address1>Copy
```

```
#Example 

wallet_get_secret_key A12uRDBsRb2vDqm1XxjuhR1VGxxxxxxxxxxxxxxxxCopy
```

Danh sách các địa chỉ ví của bạn có thể được truy cập bằng:

```
wallet_infoCopy
```

**3. Lệnh Ví (Tùy chọn)**

Nếu bạn đã có một cặp khóa từ ví trước đó, bạn có thể thêm thủ công một cặp khóa hiện có:

```
wallet_add_secret_keys <SecretKey>Copy
```

### Part06: Xếp chồng <a href="#ba00" id="ba00"></a>

**1. Yêu cầu vòi**

Tham khảo link bất hòa bên dưới trong kênh vòi testnet, nhập địa chỉ ví của bạn, bot gửi vòi tự động đến địa chỉ

### [Tham gia Massa Discord Server!](https://discord.gg/9jGhEV8B) <a href="#tham-gia-massa-discord-server" id="tham-gia-massa-discord-server"></a>

#### [Massa là một blockchain hiệu suất cao được thiết kế để thực sự phi tập trung ngay từ đầu, với 10.000 tx/s. | 37,514…](https://discord.gg/9jGhEV8B) <a href="#massa-la-mot-blockchain-hieu-suat-cao-duoc-thiet-ke-de-thuc-su-phi-tap-trung-ngay-tu-dau-voi-10-000" id="massa-la-mot-blockchain-hieu-suat-cao-duoc-thiet-ke-de-thuc-su-phi-tap-trung-ngay-tu-dau-voi-10-000"></a>

[discord.gg](https://discord.gg/9jGhEV8B)

Kiểm tra ví:

```
wallet_infoCopy
```

**2. Mua cuộn**

Mua cuộn với nó: đặt địa chỉ của bạn, số lượng cuộn bạn muốn mua và phí vận hành (bạn có thể đặt 0). Khi cuộn của bạn trở nên hoạt động, đó là nó! Bạn đang đặt cược! Xin lưu ý, có một cuộn là đủ. Trên testnet, họ không đánh giá bạn có bao nhiêu cuộn, nhưng nút của bạn đáng tin cậy như thế nào.

```
buy_rolls <address> <roll count> <fee>Copy
```

```
#Example
buy_rolls A12dr48yZaL2NpQkwsrpsNLGDpndFUCVSdYdSiQh4UfkYRMo17km 1 0Copy
```

**2. ngăn xếp**

Đăng ký địa chỉ của bạn để nút của bạn bắt đầu đặt cọc với nó:

```
node_start_staking <your_address>Copy
```

```
#Example Copy
```

```
node_start_staking A12uRDBsRb2vDqm1XxjuhR1VGxxxxxxxxxxxxxxxxCopy
```

Bây giờ bạn nên đợi một thời gian để cuộn của bạn hoạt động: 3 chu kỳ 128 chu kỳ (một chu kỳ là 32 khối – 16 giây), vì vậy khoảng 1h40 phút. Để kiểm tra thời điểm địa chỉ của bạn được chọn để đặt cọc, hãy chạy lệnh này:

```
get_addresses <your_address>Copy
```

```
#Example
get_addresses A12dr48yZaL2NpQkwsrpsNLGDpndFUCVSdYdSiQh4UfkYRMo17kmCopy
```

```
wallet_infoCopy
```

Bây giờ bạn có 4 cuộn hoạt động. Nhấn **Ctrl + A** và **D** để tách massa-client session.

### Part07: Routability <a href="#c369" id="c369"></a>

**1.Cấu hình tường lửa**

thiết lập tường lửa trên máy tính của bạn để cho phép kết nối TCP đến trên cổng 31244 và 31245.

```
ufw allow ssh 
ufw allow https 
ufw allow http 
ufw allow 31244
ufw allow 31245
ufw enableCopy
```

Khi dấu nhắc lệnh hỏi, taype **y** và nhấn **ENTER** trên bàn phím của bạn.

**2. Chỉnh sửa tệp cấu hình**

Chỉnh sửa tệp với các nội dung sau:`massa-node/config/config.toml`

trong đó AAA. BBB. CCC.DDD nên được thay thế bằng địa chỉ IP công cộng của bạn

```
nano $HOME/massa/massa-node/config/config.tomlCopy
```

```
# Copy and paste texts below to config.toml file and save it.
[network]
routable_ip = "AAA.BBB.CCC.DDD"Copy
```

```
#Example:
[network]
routable_ip = "10.20.30.40"Copy
```

Để lưu các thay đổi, hãy nhấn **Ctrl + X** sau đó nhập **Y** và nhấn **ENTER** trên bàn phím của bạn.

**3.Kiểm tra kết nối**

Sử dụng liên kết bên dưới để kiểm tra các cổng VPS của bạn:

### [Mở công cụ kiểm tra cổng – Kiểm tra chuyển tiếp cổng trên bộ định tuyến của bạn](https://www.yougetsignal.com/tools/open-ports/) <a href="#mo-cong-cu-kiem-tra-cong-kiem-tra-chuyen-tiep-cong-tren-bo-dinh-tuyen-cua-ban" id="mo-cong-cu-kiem-tra-cong-kiem-tra-chuyen-tiep-cong-tren-bo-dinh-tuyen-cua-ban"></a>

#### [Trình kiểm tra chuyển tiếp cổng là một tiện ích được sử dụng để xác định địa chỉ IP bên ngoài của bạn và phát hiện các cổng đang mở trên…](https://www.yougetsignal.com/tools/open-ports/) <a href="#trinh-kiem-tra-chuyen-tiep-cong-la-mot-tien-ich-duoc-su-dung-de-xac-dinh-dia-chi-ip-ben-ngoai-cua-ba" id="trinh-kiem-tra-chuyen-tiep-cong-la-mot-tien-ich-duoc-su-dung-de-xac-dinh-dia-chi-ip-ben-ngoai-cua-ba"></a>

[www.yougetsignal.com](https://www.yougetsignal.com/tools/open-ports/)

### Part08: Bước cuối cùng <a href="#6267" id="6267"></a>

**1.Xác thực nút:** Để xác thực sự tham gia của bạn vào chương trình phần thưởng đặt cược testnet, bạn phải đăng ký bằng tài khoản Discord của mình. Viết một cái gì đó trong kênh đăng ký testnet-rewards-của massa [Discord ](https://discord.gg/9jGhEV8B)và bot của họ sẽ gửi tin nhắn cho bạn hướng dẫn. Sao chép thông tin được chỉ định trong hình ảnh. Thay thế \<your\_staking\_address> bằng địa chỉ ví của bạn.

> Ví dụ: node\_testnet\_rewards\_program\_ownership\_proof A12uRDBsRb2vDqm1XxjuhR1VGXRaK5MipDRUmT9yBC9xxxxxx 1049040158407807026

Mở phiên màn hình liên quan đến máy khách massa và sao chép/dán thông tin vào thiết bị đầu cuối.

```
screen -r massa-clientCopy
```

<pre><code><strong>node_testnet_rewards_program_ownership_proof A12uRDBsRb2vDqm1XxjuhR1VGXRaK5MipDRUmT9yBC9xxxxxx 1049040158407807026Copy
</strong></code></pre>

Sao chép đầu ra trong bot bất hòa DM.

Chúc mừng. Nút của bạn đã kết nối thành công với tài khoản bất hòa của bạn.

**2.Một bước nữa:** Bước thứ hai là tùy chọn, nhưng có giá trị bằng một nửa số điểm của bạn. Để giúp dự án phân cấp mạng, bạn nên thiết lập nút của mình để có thể định tuyến được (Part07). Khi nút của bạn có thể định tuyến được, hãy gửi cho Massa BOT địa chỉ IP công cộng của nút của bạn. Với địa chỉ IP của bạn (và ID nút mà Massa BOT đã có), họ sẽ có thể theo dõi khi nào nút của bạn có thể truy cập được từ các nút khác!
