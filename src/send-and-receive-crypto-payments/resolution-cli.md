---
description: >-
  This page reviews the Resolution CLI option for resolving a domain. This
  option is fully supported and maintained by UD.
---

# Resolution CLI

The Resolution-CLI is built and maintained by Unstoppable Domains. It is a simple CLI tool for resolving Unstoppable domains and interacting with blockchain domain names. It can be used to retrieve [payment addresses](crypto-payments.md), IPFS hashes for [decentralized websites](../build-a-decentralized-website/overview-of-ipfs-and-d-web.md), DNS records and other [records types](../domain-registry-essentials/records-reference.md).

For more information on resolving domains using the Resolution CLI option, please see the [Resolution CLI Repository](https://github.com/unstoppabledomains/resolution-cli) on Github.

## Use Case: Retrieve the ETH Address

This will retrieve the ETH address:

```
resolution resolve addr ETH -d brad.crypto
"0x8aaD44321A86b170879d7A244c1e8d360c99DdA8"
```

The crypto.ETH.address can be located in the [Records Reference](../domain-registry-essentials/records-reference.md).

## Use Case: Retrieve a Domain Record

And this will retrieve any record from the domain, if it exists, and return the following records:

```
resolution resolve records crypto.ETH.address crypto.BTC.address -d brad.crypto
{
   "records": {
      "crypto.BTC.address": "bc1q359khn0phg58xgezyqsuuaha28zkwx047c0c3y",
      "crypto.ETH.address": "0x8aaD44321A86b170879d7A244c1e8d360c99DdA8"
   }
}
```

## Supported Domains for Resolution CLI

The Resolution CLI supports decentralized domains across three main zones:

| Name Service                   | Supported Domains                                                                      |
| ------------------------------ | -------------------------------------------------------------------------------------- |
| Zilliqa Name Service (ZNS)     | `.zil`                                                                                 |
| Ethereum Name Service (ENS)    | `.eth`, `.kred`, `.xyz`, `.luxe`                                                       |
| Unstoppable Name Service (UNS) | `.crypto`, `.nft`, `.blockchain`, `.bitcoin`, `.coin`, `.wallet,` `.888`, `.dao`, `.x` |



{% hint style="warning" %}
ENS is not supported in the latest version of our libraries, and there will be no future updates to ENS. The older version of our libraries can still be used for resolution, or developers will need to [integrate directly with ENS](https://docs.ens.domains/dapp-developer-guide/resolving-names).
{% endhint %}

## Support

If you have any questions or need assistance with using UD Resolution CLI, join our [Discord channel](https://discord.gg/b6ZVxSZ9Hn) for real-time support from us and the community.

