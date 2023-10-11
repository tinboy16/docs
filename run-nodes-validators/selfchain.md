---
description: >-
  Self Chain, a Layer 1 blockchain designed for trustless, next-generation key
  management.
---

# Selfchain

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### 1.Update system

```
sudo apt update
```

```
sudo apt-get install git curl build-essential make jq gcc snapd chrony lz4 tmux unzip bc -y
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Result for update</p></figcaption></figure>

#### 2.Install Go

```
rm -rf $HOME/go
sudo rm -rf /usr/local/go
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

```
cd $HOME
curl https://dl.google.com/go/go1.20.5.linux-amd64.tar.gz | sudo tar -C/usr/local -zxvf -
cat <<'EOF' >>$HOME/.profile
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
EOF
source $HOME/.profile
go version
```

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

#### 3.Install node

```
cd $HOME
```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

```
mkdir -p /root/go/bin/
```

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

```
wget https://ss-t.self.nodestake.top/selfchaind
```

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

```
chmod +x selfchaind
```

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

```
mv selfchaind /root/go/bin/
```

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

#### 4. Initialize Node

**Initiate the node**

```
selfchaind init NodeName --chain-id=self-dev-1
```

Replace: Nodename = Your Moniker, example Nodename = VNBnode

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

**Download Genesis**

```
curl -Ls https://github.com/Adamtruong6868/Selfchain.xyz/blob/main/genesis.json > $HOME/.selfchain/config/genesis.json
```

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

**Download addrbook**

```
curl -Ls https://github.com/Adamtruong6868/Selfchain.xyz/blob/main/addrbook.json > $HOME/.selfchain/config/addrbook.json
```

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

**Create Service**

```
ExplainExplainsudo tee /etc/systemd/system/selfchaind.service > /dev/null <<EOF
[Unit]
Description=selfchaind Daemon
After=network-online.target
[Service]
User=$USER
ExecStart=$(which selfchaind) start
Restart=always
RestartSec=3
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
sudo systemctl daemon-reload
sudo systemctl enable selfchaind
```

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

**Run Node**

```
sudo systemctl restart selfchaind
```

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

**Check synch**

```
journalctl -u selfchaind -f
```

**Create the keys**

```
selfchaind keys --home ~/.selfchain --keyring-backend file --keyring-dir keys add <key_name>
```

Replace \<Key\_name> by your node name. Example VNBnodes.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Enter your strong passphrase 2 times. The result should be like this:

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

The wallet address start with “self…..”, keep it for the next steps.

example: self1yrvg0zahdy76c9z2gwjuqy8x2d7eyhw5xa8zn7

**Modify the Denomination and Minimum Gas**

```
nano ~/.selfchain/config/app.toml
```

You will see this screen\


<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

change “0stake” —> "0.005uself" like this

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Find this location

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Change “uatom” —> “uself” like this

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Find the API configuration

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

change these 2 falses —> true, like this

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Once you completed, press Ctr + O, then enter to save file.

Ctrl + X to escape.

**Modify the Config.toml file**

```
nano .selfchain/config/config.toml
```

You will see this screen

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

Find this laddr location

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

change it —> “tcp://0.0.0.0:26657”

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

Press Ctr + O, then enter to save file. Then Ctrl + X to escape.

**Modify chain ID**

```
cd ~/.selfchain/config
```

```
nano client.toml
```

you will see this

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

change it to “self-dev-1”

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

Press Ctr + O, then enter to save file. Then Ctrl + X to escape.

**Stop node and restart again**

```
sudo systemctl stop selfchaind
```

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

then

```
sudo systemctl restart selfchaind
```

**Check synch status:**

```
selfchaind status
```

The return should be like this:

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

**Once you see the “catching\_up”:false, that means the node is synched. If it’s true, then just wait until the node synched.**

**Go to discord and faucet**

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

The token shall be sent manually by team, keep patient.

To check the balance of token, go to your terminal and check command to see the balance.

```
selfchaind q bank balances YOUR_WALLET_ADDRESS
```

**Create Validator**

After the node is synched, and faucet successfully. You need to do the TX to create the validator.

```
Explainselfchaind tx staking create-validator \
--amount=100000000uself \
--pubkey=$(selfchaind tendermint show-validator) \
--moniker="your node name" \
--identity="keybase ID" \
--details="The information about yourself that you want to share" \
--security-contact="" \
--website="Your website if any" \
--chain-id=self-dev-1 \
--commission-rate=0.15 \
--commission-max-rate=0.20 \
--commission-max-change-rate=0.1 \
--min-self-delegation=1 \
--gas-adjustment 1.5 \
--from=your_wallet_address \
--fees=1000uself \
-y
```

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Enter your passphrase to confirm TX. You will see this:

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

Copy the TXhash and go to Discord to register with the BOT.

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

Once you completed, go to explorer to check your node (after the team approved)\
\


<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

To stake more for your node, use this command

```
selfchaind tx staking delegate $(selfchaind keys show YOUR_WALLET_ADDRESS --bech val -a) 1000000uself --from YOUR_WALLET_ADDRESS --chain-id self-dev-1 --gas-adjustment 1.2 --fees 1000uself -y
```

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

Visit our communities:

Telegram group chat: [https://VNBnodechat](https://t.me/+4aLsnP6JHhY4YTY1)

Telegram news channel: [https://VNBnode\_news](https://t.me/+IpfWe\_pX7UlkMzY1)

Web: [https://VNBnode.com](https://vnbnode.com)&#x20;
