# Guide to install Roller - Dymension

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption><p>Guide to install Rollapps and Deploy NFT smart contract</p></figcaption></figure>

**Minimum hardware requirements**:

CPU: 2 cores.

Disk: 500 GB SSD (recommend NVME or SSD).

Ram: 16GB.

**Step 1**: Update libraries:

```
sudo apt update && sudo apt upgrade -y
```

**Step 2**: Install Roller

```
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

<figure><img src=".gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

**Step 3**: Check version of Roller​

```
roller version
```

**Step 4**: Initiate Roller

```
roller config init --interactive
```

<figure><img src=".gitbook/assets/image (29).png" alt=""><figcaption><p>Choose froopyland</p></figcaption></figure>

**Enter your RollApp ID**

1. Using this format to name your RollApp:&#x20;

* Lowercase English letters
* Example: vnbnode or tothemoon

2. Specify your RollApp denom:

Name your native token as you want:&#x20;

* Example: VNB or BCT or NICE…

3. Set the genesis token supply:

* This is the initial token supply in the RollApp (default: 1,000,000,000).
* It’s up to you to define the quantity.

4. Select Data Availability layer

As default there are 2 DA layers: Celestia and Avail to select.

<figure><img src=".gitbook/assets/image (30).png" alt=""><figcaption><p>You can choose Celestia or Avail</p></figcaption></figure>

5.  Select your execution environment:

    As default is EVM or custom (RDK).

<figure><img src=".gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

One you finished, it will return to you 3 address as below:

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Copy 3 addresses and go to [Discord Froopyland](https://discord.com/channels/956961633165529098/1143231362468434022) to claim faucets as below:

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

For Celestia address go to [celestia-faucet](https://discord.com/channels/956961633165529098/1128048548999610451):&#x20;

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

After that check the balance in your wallets:

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Step 5**: Register for Roller

```
roller register
```

Result should be:

![](<.gitbook/assets/image (6).png>)\


**Step 6**: Run the Roller

run command:

```
tmux
```

and then

```
roller run
```

Result should be:

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Wait for about 10-15 minutes to active the Relayer. Once it’s active, you will see like this:

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

To escape : press combination: ctrl+b, then d.

**Step 7**: Do the interact via IBC transfer

**Step 7**: Do the interact via IBC transfer

```
rollapp_evm tx ibc-transfer transfer transfer channel-0 dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 1000000000000000000uVNB --from rollapp_sequencer --keyring-backend test --home ~/.roller/rollapp --broadcast-mode block
```

**Note:** uVNB should inline with your native token that you created in item 2, Step 4. As default 18 additional decimal places, mean 1 VNB = 1000,000,000,000,000,000 uVNB.

You will be asked to confirm as below: Just type Y and go ahead.

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

**Step 8**: Export keys

```
roller keys list
```

The result should be like this:

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

To export private keys, use the following commands (one by one):

```
roller keys export hub_sequencer
```

Then:

```
roller keys export rollapp_sequencer
```

and:

```
roller keys export my_celes_key
```

The results should be like:

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Save these private keys in your private location (do not let someone see it).

**Step 9**: Import to Metamask

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Copy and paste your roller-sequencer private key (from step 8) here:

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

**Step 10**: Add Roller network

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

**Network name**: Your Rollapp ID

**New RPC URL**: Your\_IP\_address : 8545

**Chain ID**: The **EIP155** number in your Rollapp ID.

**Currency symbol**: Your RollApp denom

Example: For Rollapp ID: **vnbnode\_1234-1**

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Once finished, you will see it like this:

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

**Step 11**: Create a NFT smart contract

Access to [Remix](https://remix.ethereum.org/#lang=en\&optimize=false\&runs=200\&evmVersion=null\&version=soljson-v0.8.20+commit.a1b79de6.js).

Then you will see a page like this:

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

click on the contract folder to create new file:

<figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Name it as: NFT.sol

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

in the content of NFT.sol, just copy and paste as below:

**Note**: in constructor: replace \_name; \_symbol as you want for NFT.

```
// SPDX-License-Identifier: UNLICENSED

pragma solidity 0.8.19;

import "https://github.com/transmissions11/solmate/blob/main/src/tokens/ERC721.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/Strings.sol";

contract NFT is ERC721 {
    uint256 public currentTokenId;

    constructor(
        string memory _name,
        string memory _symbol
    ) ERC721(_name, _symbol) {}

    function mintTo(address recipient) public payable returns (uint256) {
        uint256 newItemId = ++currentTokenId;
        _safeMint(recipient, newItemId);
        return newItemId;
    }

    function tokenURI(uint256 id) public view virtual override returns (string memory) {
        return Strings.toString(id);
    }
}
```

Example: \_name = vnbnode

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

**Step 12**: Comply the smart contract

If you can see the green check, that means it’s ok.

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

**Step 13**: Deploy and run Smart contract

Select Injected Provider - Metamask as below:

<figure><img src=".gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

it will popup metamask wallet, select the Account that you imported before and click next:

<figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Select contract NFT.sol

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Click the Deploy button and confirm transaction on metamask.

<figure><img src=".gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

**Step 14**: Play with NFT

Insert minTo and balanceOf, as your Metamask wallet. It’s time to play with NFT contract.

<figure><img src=".gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

**Check log:**

**Log rollapp:**

tail -f .roller/rollapp/rollapp.log

**Log Relayer:**

tail -f .roller/relayer/relayer.log

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

Visit our communities:

Telegram group chat: [https://VNBnodechat](https://t.me/+4aLsnP6JHhY4YTY1)

Telegram news channel: [https://VNBnode\_news](https://t.me/+IpfWe\_pX7UlkMzY1)

Web: [https://VNBnode.com](https://vnbnode.com)&#x20;
