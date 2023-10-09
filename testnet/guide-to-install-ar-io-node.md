---
cover: >-
  https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb424cf1c-9ca0-478f-990c-5856afd4030d_592x308.png
coverY: 0
---

# Guide to install AR io node

Hệ sinh thái AR.IO cam kết phát triển các sản phẩm và giao thức để duy trì việc truy cập vào tính bền vững của dữ liệu kỹ thuật số, giúp cho permaweb trở nên dễ dàng tiếp cận với mọi người. Mạng lưới toàn cầu của các Gateway này kết nối người dùng đến dữ liệu, tệp tin, ứng dụng và trang web được lưu trữ vĩnh viễn trên mạng lưu trữ phi tập trung Arweave.

## **Minimum requirements**

* 4 core CPU
* 4 GB Ram
* 500 GB storage (SSD recommended)
* Stable 50 Mbps internet connection

### **Recommended**

* 12 core CPU
* 32 GB Ram
* 2 TB SSD storage
* Stable 1 Gbps internet connection

### **Step 1: Install packages**

{% code overflow="wrap" %}
```
sudo apt update -y && sudo apt upgrade -y && sudo apt install -y curl openssh-server docker-compose git certbot nginx sqlite3 build-essential && sudo systemctl enable ssh && curl -sSL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - && echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list && sudo apt-get update -y && sudo apt-get install -y yarn && curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash && source ~/.bashrc && sudo ufw allow 22 80 443 && sudo ufw enable
```
{% endcode %}



<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```
nvm install 16.15.1 && nvm use 16.15.1
```
{% endcode %}

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### **Step 2: Update your software:**

```
sudo apt update
sudo apt upgrade
```



### **Step 3: Open your ports**

```
sudo ufw disable
```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

```
sudo ufw default allow
```

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

```
sudo ufw allow ssh
```

<figure><img src="../.gitbook/assets/741a15ab-a008-4b5d-8892-b860287411b3_1503x131.webp" alt=""><figcaption></figcaption></figure>

```
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
```

<figure><img src="../.gitbook/assets/d95c544d-cf70-4f1c-8e4b-b3f37588b891_1503x295.webp" alt=""><figcaption></figcaption></figure>

```
sudo ufw enable
```

<figure><img src="../.gitbook/assets/d9931580-7bf8-44b6-92d8-96fb35fc2682_1500x126.webp" alt=""><figcaption></figcaption></figure>

```
sudo ufw status numbered
```



### **Step 4: Install nginx:**

```
sudo apt install nginx -y
```

<figure><img src="../.gitbook/assets/9a0eca80-6978-4440-a4d9-db7e45899496_1501x287 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 5: Install git:**

```
sudo apt install git -y
```

### **Step 6: Install docker:**

{% code overflow="wrap" %}
```
sudo apt install docker-compose -y
```
{% endcode %}



* Test Docker installation:

```
sudo docker run hello-world
```

<figure><img src="../.gitbook/assets/81369c1b-939f-4b4f-b880-de0ae53a898d_1503x676 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 7: Install Certbot:**

```
sudo apt install certbot -y
```

<figure><img src="../.gitbook/assets/d5374f8c-04c9-4465-ad4b-f3579024e3a8_1502x282 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 8: Install ssh**

{% code overflow="wrap" %}
```
sudo apt install openssh-server -y
sudo systemctl enable ssh
```
{% endcode %}

<figure><img src="../.gitbook/assets/81216aa8-224b-4ef2-bb37-47a7b4428bb0_1508x378 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 9: Install Yarn:**

{% code overflow="wrap" %}
```
curl -sSL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -      echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```
{% endcode %}

```
sudo apt-get update -y
```

```
sudo apt-get install yarn -y
```

<figure><img src="../.gitbook/assets/f53db337-808a-4b66-9d33-e34470b44abb_1496x741 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 10: Install NVM (Node Version Manager):**

{% code overflow="wrap" %}
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash source ~/.bashrc
```
{% endcode %}

<figure><img src="../.gitbook/assets/9b39318f-e129-43f3-bfe9-271ed7032d96_1508x452 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 11: Install Node.js:**

```
nvm install 16.15.1
```

<figure><img src="../.gitbook/assets/740d162b-a9f3-4255-b618-6f558ff81cce_1507x133 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 12: Install build tools**

```
sudo apt install build-essential
```

<figure><img src="../.gitbook/assets/35a3b893-5672-4358-b54a-425dcca0878c_1508x293 (1).webp" alt=""><figcaption></figcaption></figure>

#### **Step 13: Install SQLite:**

```
sudo apt install sqlite3 -y
```

<figure><img src="../.gitbook/assets/93563083-debc-43eb-986d-57a3749bd2a1_1506x281 (1).webp" alt=""><figcaption></figcaption></figure>

## Install the Node

### **Step 14: Clone the ar-io-node repository and navigate into it:**

```
git clone https://github.com/ar-io/ar-io-node
cd ar-io-node
```

<figure><img src="../.gitbook/assets/d25997ea-ccfb-43a1-9e8f-d591c47ec5e0_1502x292 (1).webp" alt=""><figcaption></figcaption></figure>

**Step 15: Create an environment file:**

```
nano .env
```

<figure><img src="../.gitbook/assets/1b7bccd3-de85-4ce5-888a-54179341880d_1500x49 (1).webp" alt=""><figcaption></figcaption></figure>

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

### **Step 16: Build the Docker container:**

{% code overflow="wrap" %}
```
sudo docker-compose up -d --build
```
{% endcode %}

<figure><img src="../.gitbook/assets/639dc660-76be-45bd-9bea-6e66d85f1956_1488x854 (1).webp" alt=""><figcaption></figcaption></figure>

### **Step 17: Check the logs for errors:**

{% code overflow="wrap" %}
```
sudo docker-compose logs -f --tail=0
```
{% endcode %}

<figure><img src="../.gitbook/assets/fa380978-09e9-4fcc-8980-71afce4b8268_1492x497 (1).webp" alt=""><figcaption></figcaption></figure>

