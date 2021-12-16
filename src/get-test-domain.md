---
description: >-
  This page describes the process for requesting a free test domain as a
  developer using the Unstoppable Website faucet, Etherscan (direct contract
  calling), and Polygonscan (direct contract calling).
---

# Get A Test Domain

To make integrations easier, Unstoppable Domains provides developers with a free test domain. You can use any available domain extension for your free test domain (except .zil).&#x20;

To distinguish these test domains from paid domains, all test domains are prefixed with `udtestdev-`. For example:

* `udtestdev-freedomainisawesome.crypto`
* `udtestdev-test-wallet-integration.wallet`

To prevent abuse, we ask that developers cover the cost of minting and transferring these domains to their wallets. **Unstoppable Domains does not make any money from issuing test domains.**

{% hint style="info" %}
[Rinkeby faucet](https://faucet.rinkeby.io) and [Polygon faucet](https://faucet.polygon.technology) both offer free money - Ether and matic tokens -  for domains minted on Rinkeby Testnet and Polygon Testnet, respectively. Please see the guides below for more detailed information.
{% endhint %}

## Test Domain Options

Free test domains are available via three different methods:&#x20;

* [Unstoppable Website Faucet](get-test-domain.md#get-a-domain-using-unstoppable-website-faucet)
* [Etherscan test domain](get-test-domain.md#get-a-domain-using-etherscan), through direct smart contract calling
* [Polygonscan test domain](get-test-domain.md#get-a-domain-using-polygonscan), through direct smart contract calling

## Get a domain using Unstoppable Website faucet

### Step 1: Gather Requirements for the Website Faucet

* A web3 compatible wallet
* [Configure your wallet for Rinkeby Testnet](get-test-domain.md#step-1-gather-requirements-for-etherscan) or [Configure your wallet for Polygon/Mumbai](get-test-domain.md#step-1.-configure-your-metamask-wallet)
* [Get free Ether from Rinkeby faucet](get-test-domain.md#step-2.-get-matic-tokens-though-the-faucet) or [Get free MATIC tokens from Polygon faucet](get-test-domain.md#step-2.-get-matic-tokens-though-the-faucet-1) to cover transaction fees (only for domains minted on testnet)

{% hint style="info" %}
Domains on Polygon Mainnet can be purchased for free through Unstoppable Website Faucet, but users will need to cover their own gas fees to mint the domain.
{% endhint %}

### Step 2: Configure the Test Domain

* Go to the [Unstoppable Website Faucet](https://unstoppabledomains.com/developers) page for developers.
* Select the network for the domain: **Rinkeby Testnet**, **Polygon Mainnet,** or **Mumbai Testnet**.
* Configure the domain options:
  * **domain extension**: .888, .crypto, .x, .coin, .wallet, .bitcoin, .nft, .dao
  * **domain suffix**: the part of the domain the follows `udtestdev-`
  * **recipient address**: must enter ETH address (required)
  * **cryptocurrency records**: add optional cryptocurrency addresses, such as bitcoin or litecoin
  * **custom records**: add optional key and value pairs

![Configure options on Unstoppable website faucet](.gitbook/assets/website-faucet-options.png)

{% hint style="info" %}
If you don't know the recipient address, this information will be retrieved and populated for you after connecting your wallet to the transaction. Just click on **Mint Domain** to continue.
{% endhint %}

### Step 3: Mint the Domain & Sign the Transaction

* Click the **Mint Domain** button when finished configuring options.
* Sign the transaction with your wallet.

{% hint style="success" %}
Congratulations! You're the new proud owner of a test domain on your preferred network. Happy hacking!
{% endhint %}

## Get a domain using Etherscan

### Step 1: Configure your MetaMask wallet for Etherscan

* Configure [MetaMask](https://metamask.io) or any wallet with [WalletConnect](https://walletconnect.org/wallets) support.
* Ensure you have Ether on your Ethereum wallet to pay transaction fees.

{% hint style="info" %}
To calculate the transaction fee you'd like to target you can use services like [ETH Gas Station](https://ethgasstation.info/calculatorTxV.php). The average transaction gas usage to mint and transfer a new domains is around 180,000 gas.
{% endhint %}

### Step 2. Get free Ether from Rinkeby Faucet

* Go to Faucet Page: [https://faucet.rinkeby.io/](https://faucet.rinkeby.io).
* Make a Twitter or Facebook post with your Ethereum address pasted anywhere in the contents of the post.
* Copy/paste the URL of the post to Rinkeby faucet to verify your identity.
* Click the **Give Me Ether** button.

![Retrieve free Ether through the faucet to cover gas fees for domains on Rinkeby testnet (Layer 1)](.gitbook/assets/rinkeby-faucet-free-ether.png)



### Step 3: Open the Etherscan Smart Contract Request

* Open the domain request Smart Contract using [Etherscan](https://etherscan.io/address/0x1fC985cAc641ED5846b631f96F35d9b48Bc3b834#writeContract).
* To get a test domain on testnet, find the Smart Contract address in [reference table](domain-registry-essentials/cns-smart-contracts.md#freeminter).
* Connect your wallet.

![How to locate the smart contract address in the reference table and connect your wallet](.gitbook/assets/etherscan-steps-test-domain.png)

### Step 4: Write the Etherscan Smart Contract Request

* Enter the **suffix** for the domain in the claim -> label (string) field.
* &#x20;Press the **Write** button to start the transaction.

![Select the suffix for the domain and click "Write" button to start the transaction](../.gitbook/assets/step-3.png)

* Sign the transaction.

![Etherscan wallet signature page](.gitbook/assets/step-4-etherscan-claim-domain.png) ![Etherscan error for insufficient funds](.gitbook/assets/step-4-1-etherscan-claim-domain.png)

{% hint style="danger" %}
If a transaction takes more gas than expected (more than 200,000 gas to call the claim method) or fails, that domain name may be already claimed. Double check that it's available and [contact us](https://discord.gg/b6ZVxSZ9Hn) if you continue to have problems.&#x20;
{% endhint %}

{% hint style="success" %}
Congratulations! You're the new proud owner of a test domain on Etherscan. Happy hacking!
{% endhint %}

## Get a domain using Polygonscan

### Step 1. Configure your Metamask wallet for Polygon

* Go to [**Metamask**](https://metamask.io) **→ Settings → Networks.**
* Press **Add Network** button.
* Fill fields with the following values:
  * **Network Name:** Mumbai
  * **New RPC URL:** [https://polygon-mumbai.infura.io/v3/4458cf4d1689497b9a38b1d6bbf05e78](https://polygon-mumbai.infura.io/v3/4458cf4d1689497b9a38b1d6bbf05e78)
  * **Chain ID:** 80001
  * **Currency Symbol:** MATIC
  * **Block Explorer URL:** [https://mumbai.polygonscan.com](https://mumbai.polygonscan.com)

![Configure network settings in MetaMask to use Polygonscan domains (Layer 2)](.gitbook/assets/configure-metamask-polygonscan.png)

### Step 2. Get free MATIC tokens from Polygon Faucet

* Go to Faucet Page: [https://faucet.polygon.technology/](https://faucet.polygon.technology).
* Choose MATIC token and Mumbai network.
* Enter your wallet address.
* Click **Submit** button.

![Retrieve free MATIC tokens through the faucet to cover gas fees for domains on Mumbai testnet (Layer 2)](.gitbook/assets/polygon-free-matic-tokens.png)

### Step 3: Locate the TLD namehash for Polygon

* TLD namehash can be found by using the website API:
  * .wallet TLD -[https://unstoppabledomains.com/api/v1/wallet](https://unstoppabledomains.com/api/v1/wallet)
  * .888 TLD -[https://unstoppabledomains.com/api/v1/888](https://unstoppabledomains.com/api/v1/888)
  * .dao TLD -[https://unstoppabledomains.com/api/v1/dao](https://unstoppabledomains.com/api/v1/dao)

For example, the API response for .dao TLD 4amehash is `0xb5f2bbf81da581299d4ff7af60560c0ac854196f5227328d2d0c2bb0df33e553`.

```json
{
  "addresses": {},
  "multicoinAddresses": {},
  "whois": {},
  "ipfs": {},
  "social": {},
  "dns": [],
  "meta": {
    "domain": "dao",
    "namehash": "0xb5f2bbf81da581299d4ff7af60560c0ac854196f5227328d2d0c2bb0df33e553",
    "tokenId": "82297499899003349669721577255820055932923117933045045557665992854629036320083",
    "owner": null,
    "resolver": null,
    "type": "CNS",
    "ttl": 0
  },
  "records": {}
}
```

* Or, you can locate the TLD namehash in the following list:

```json
0x0f4a10a4f46c288cea365fcf45cccf0e9d901b945b9829ccdb54c10dc3cb7a6f = 'crypto';
0xb5f2bbf81da581299d4ff7af60560c0ac854196f5227328d2d0c2bb0df33e553 = 'wallet';
0x7674e7282552c15f203b9c4a6025aeaf28176ef7f5451b280f9bada3f8bc98e2 = 'coin';
0x241e7e2b7fd7333b3c0c049b326316b811af0c01cfc0c7a90b466fda3a70fc2d = 'x';
0xb75cf4f3d8bc3deb317ed5216d898899d5cc6a783f65f6768eb9bcb89428670d = 'nft';
0x4118ebbd893ecbb9f5d7a817c7d8039c1bd991b56ea243e2ae84d0a1b2c950a7 = 'blockchain';
0x042fb01c1e43fb4a32f85b41c821e17d2faeac58cfc5fb23f80bc00c940f85e3 = 'bitcoin';
0x5c828ec285c0bf152a30a325b3963661a80cb87641d60920344caf04d4a0f31e = '888';
0xb5f2bbf81da581299d4ff7af60560c0ac854196f5227328d2d0c2bb0df33e553 = 'dao';
```

### Step 4: Write the Polygonscan Smart Contract Request

* Go to [Polygonscan/Mumbai](https://mumbai.polygonscan.com/address/0x428189346bb3CC52f031A1092fd47C919AC30A9f#writeProxyContract) Smart Contract Page
* Choose **Write as Proxy** tab
* Connect your wallet (Rinkeby)
* Choose `claimToWithRecords` method and fill properties with needed values: receiver wallet address, TLD namehash, and test domain suffix.

![Enter data for 'claim to records' for Polygonscan domain (Layer2)](.gitbook/assets/polygonscan-claim-to-records.png)

* Click the **Write** button to start the transaction.&#x20;

{% hint style="success" %}
Congratulations! You're the new proud owner of a test domain on Polygon Mumbai testnet. Happy hacking!
{% endhint %}
