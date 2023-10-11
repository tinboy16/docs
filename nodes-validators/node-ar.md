# Node AR

Telegram: [https://t.me/VNBnodegroup](https://t.me/VNBnodegroup)

X (Twitter): [https://x.com/vnbnode](https://x.com/vnbnode)

Hệ sinh thái AR.IO cam kết phát triển các sản phẩm và giao thức để duy trì việc truy cập vào tính bền vững của dữ liệu kỹ thuật số, giúp cho permaweb trở nên dễ dàng tiếp cận với mọi người. Mạng lưới toàn cầu của các Gateway này kết nối người dùng đến dữ liệu, tệp tin, ứng dụng và trang web được lưu trữ vĩnh viễn trên mạng lưu trữ phi tập trung Arweave.

* 4 core CPU
* 4 GB Ram
* 500 GB storage (SSD recommended)
* Stable 50 Mbps internet connection
* 12 core CPU
* 32 GB Ram
* 2 TB SSD storage
* Stable 1 Gbps internet connection

```
sudo apt update -y && sudo apt upgrade -y && sudo apt install -y curl openssh-server docker-compose git certbot nginx sqlite3 build-essential && sudo systemctl enable ssh && curl -sSL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - && echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list && sudo apt-get update -y && sudo apt-get install -y yarn && curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash && source ~/.bashrc && sudo ufw allow 22 80 443 && sudo ufw enable
```

```
nvm install 16.15.1 && nvm use 16.15.1
```

```
sudo apt update
sudo apt upgrade
```

```
sudo ufw disable
```

```
sudo ufw default allow
```

```
sudo ufw allow ssh
```

```
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
```

```
sudo ufw enable
```

```
sudo ufw status numbered
```

```
sudo apt install nginx -y
```

```
sudo apt install git -y
```

```
sudo apt install docker-compose -y
```

* Test Docker installation:

```
sudo docker run hello-world
```

```
sudo apt install certbot -y
```

```
sudo apt install openssh-server -y
sudo systemctl enable ssh
```

```
curl -sSL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -      echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

```
sudo apt-get update -y
```

```
sudo apt-get install yarn -y
```

{% code overflow="wrap" %}
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash source ~/.bashrc
```
{% endcode %}

```
nvm install 16.15.1
```

```
sudo apt install build-essential
```

```
sudo apt install sqlite3 -y
```

```
git clone https://github.com/ar-io/ar-io-node
cd ar-io-node
```

```
nano .env
```

Paste the following into the file and save.

```
GRAPHQL_HOST=arweave.net
GRAPHQL_PORT=443
START_HEIGHT=1000000
ARNS_ROOT_HOST=<your-domain>
```

Replace \<your-domain> with the domain address, for your node.

To get free domain, you can try: [https://www.hostinger.com/free-domain](https://www.hostinger.com/free-domain) or other sources.

With VPS, you can try with

```
 hostname -f
```

```
sudo docker-compose up -d --build
```

```
sudo docker-compose logs -f --tail=0
```

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

Research and translate by VNBnodes - A professional group with experienced validators/researchers. We are proud to be partner of many blockchain projects, to share the aim to bring securities to blockchain industry and educate the blockchain technologies to non-technical users.

Visit us [VNBnodes](https://linktr.ee/vnbnodes) at:

Telegram news: [https://t.me/Vnbnode](https://t.me/Vnbnode)

Telegram Chat group: [t.me/VNBnodegroup](http://t.me/VNBnodegroup)
