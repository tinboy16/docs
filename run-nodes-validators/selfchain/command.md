# Command

Telegram: [https://t.me/VNBnodegroup](https://t.me/VNBnodegroup)

X (Twitter): [https://x.com/vnbnode](https://x.com/vnbnode)

Key management&#x20;

Add New Wallet

```
selfchaind keys add wallet
```

Restore executing wallet

```
selfchaind keys add wallet --recover
```

List All Wallets

```
selfchaind keys list
```

Delete wallet

```
selfchaind keys delete wallet
```

Check Balance

```
selfchaind q bank balances $(selfchaind keys show wallet -a)
```

Export Key (save to wallet.backup)

```
selfchaind keys export wallet
```

Import Key (restore from wallet.backup)

```
selfchaind keys import wallet wallet.backup
```

Create New Validator

```
selfchaind tx staking create-validator \
--amount 1000000uself \
--pubkey $(selfchaind tendermint show-validator) \
--moniker "MONIKER" \
--identity "KEYBASE_ID" \
--website "YOUR WEBSITE" \
--details "YOUR DETAILS" \
--chain-id self-dev-1 \
--commission-rate 0.05 \
--commission-max-rate 0.20 \
--commission-max-change-rate 0.01 \
--min-self-delegation 1 \
--from wallet \
--gas-adjustment 1.4 \
--gas auto \
--gas-prices 0.005uself \
-y
```

Edit Existing Validator

```
selfchaind tx staking edit-validator \
--new-moniker "YOUR_MONIKER_NAME" \
--identity "YOUR_KEYBASE_ID" \
--details "YOUR_DETAILS" \
--website "YOUR_WEBSITE_URL"
--chain-id self-dev-1 \
--commission-rate 0.05 \
--from wallet \
--gas-adjustment 1.4 \
--gas auto \
--gas-prices 0.005uselfchain \
-y
```

Withdraw all rewards

```
selfchaind tx distribution withdraw-all-rewards --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Withdraw rewards and commission from your validator

```
selfchaind tx distribution withdraw-rewards $(selfchaind keys show wallet --bech val -a) --commission --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Delegate to Yourself

```
selfchaind tx staking delegate $(selfchaind keys show wallet --bech val -a) 1000000uselfchain --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Delegate

```
selfchaind tx staking delegate <TO_VALOPER_ADDRESS> 1000000uselfchain --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Redelegate Stake to Another Validator

```
selfchaind tx staking redelegate $(selfchaind keys show wallet --bech val -a) <TO_VALOPER_ADDRESS> 1000000uselfchain --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Unbond

```
selfchaind tx staking unbond $(selfchaind keys show wallet --bech val -a) 1000000uselfchain --from wallet --chain-id selfchainru-itn-1 --gas-adjustment 1.4 --gas auto --gas-prices 0.005uselfchain -y
```

Transfer Funds

```
selfchaind tx bank send wallet <TO_WALLET_ADDRESS> 1000000uselfchain --from wallet --chain-id selfchainru-itn-1
```

Validator info

```
selfchaind status 2>&1 | jq .ValidatorInfo
```

Validator Details

```
selfchaind q staking validator $(selfchaind keys show wallet --bech val -a)
```

Jailing info

```
selfchaind q slashing signing-info $(selfchaind tendermint show-validator)
```

Unjail validator

```
selfchaind tx slashing unjail --from wallet --chain-id self-dev-1 --gas-prices=0.005uself --gas-adjustment 1.5 --gas auto -y
```

Active Validators List

```
selfchaind q staking validators -oj --limit=3000 | jq '.validators[] | select(.status=="BOND_STATUS_BONDED")' | jq -r '(.tokens|tonumber/pow(10; 6)|floor|tostring) + " \t " + .description.moniker' | sort -gr | nl 
```

Check Validator key

```
selfchaind q staking validator $(selfchaind  keys show wallet --bech val -a) 
```

Signing info

<pre><code><strong>selfchaind query slashing signing-info $(selfchaind tendermint show-validator) 
</strong></code></pre>

Create new text proposal

```
selfchaind tx gov submit-proposal \
--title="Title" \
--description="Description" \
--deposit=100000000uself \
--type="Text" \
--from=wallet \
--gas-prices 0.005uself\ 
--gas-adjustment 1.5 \
--gas auto \
-y 
```

List all proposals

```
mantrachaind query gov proposals
```

Vote 'Yes'

```
selfchaind tx gov vote 1 yes --from wallet --chain-id self-dev-1 --gas-prices=0.005uself --gas-adjustment 1.5 --gas auto -y
```

Vote 'No'

```
mantrachaind tx gov vote 1 no --from wallet --chain-id self-dev-1 --gas-prices=0.005uself --gas-adjustment 1.5 --gas auto -y
```

Vote 'Abstain'

```
mantrachaind tx gov vote 1 abstain --from wallet --chain-id self-dev-1 --gas-prices=0.005uself --gas-adjustment 1.5 --gas auto -y
```

Vote 'NoWithVeto'

```
mantrachaind tx gov vote 1 nowithveto --from wallet --chain-id self-dev-1 --gas-prices=0.005uself --gas-adjustment 1.5 --gas auto -y
```

Remove node

```
cd $HOME
sudo systemctl stop selfchaind
sudo systemctl disable selfchaind
sudo rm /etc/systemd/system/selfchaind.service
sudo systemctl daemon-reload
rm -f $(which selfchaind)
rm -rf $HOME/.selfchaind
rm -rf $HOME/selfchain
```

Visit our communities:

Telegram group chat: [https://VNBnodechat](https://t.me/+4aLsnP6JHhY4YTY1)

Telegram news channel: [https://VNBnode\_news](https://t.me/+IpfWe\_pX7UlkMzY1)

Web: [https://VNBnode.com](https://vnbnode.com)&#x20;
