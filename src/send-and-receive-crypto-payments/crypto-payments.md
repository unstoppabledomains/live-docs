---
description: >-
  This page reviews the process for sending and receiving crypto payments on
  Ethereum, Zilliqa, and Unstoppable blockchains.
---

# Crypto Payments

## Table of contents

* [Overview](crypto-payments.md#overview)
* [Domain Resolution using Libraries](crypto-payments.md#enabling-domain-resolution)
  * [Resolving crypto records](crypto-payments.md#resolving-crypto-records)
  * [Error handling](crypto-payments.md#error-handling)
* [Domain Resolution using Resolution Service API](crypto-payments.md#domain-resolution-using-resolution-service)
* [Best practices](crypto-payments.md#integration-best-practices)
* [Resources](crypto-payments.md#resources)

## Overview

The most common way to integrate with Unstoppable Domains is through simple domain resolution. This process converts a human-readable name like `brad.crypto` to the cryptocurrency addresses that name stores. As long as the addresses are set, a user can send any of our 80+ supported cryptocurrencies to an Unstoppable Domain and it will end up in the right place. A user can send `BTC` to `brad.crypto` and it will go to Brad's `BTC` address. A user can send `ETH` to `brad.crypto` and will go to Brad's `ETH` address. Unstoppable Domains support 80+ cryptocurrencies and counting.

![A successful domain resolution and payment](../.gitbook/assets/success-payment-example.gif)

How does this work?

At a high-level, an application retrieves a domain's records through smart contracts deployed on the Ethereum, Zilliqa, and Unstoppable blockchains \(`.crypto`, `.zil`, and `.wallet`, respectively\).

In the example above, we're sending 1 `ETH` to `ryan.crypto`. The application sends those two parameters to the `Resolver` contract on the Ethereum blockchain and it returns the record stored under `crypto.ETH.address` for that domain. This address can be used to complete the `ETH` transfer to Ryan.

{% hint style="info" %}
A domain can store many records and key formats. To learn about our supported record types, see [Records reference guide](../domain-registry-essentials/records-reference.md).
{% endhint %}

![Data movement for a successful payment](../.gitbook/assets/success-payment-flow.svg)

## Domain Resolution with Libraries

The easiest way to integrate domain resolution for crypto payments is by using the Unstoppable Domains resolution libraries. These libraries communicate with the Ethereum and Zilliqa blockchains directly so that you don't have to.

### Resolving crypto records

#### Example: Resolving `ryan.crypto` into Ethereum address

To resolve `ryan.crypto` into its Ethereum address, the library searches for the `crypto.ETH.address` record attached to the domain.

{% tabs %}
{% tab title="resolution" %}
```javascript
const {default: Resolution} = require('@unstoppabledomains/resolution');
const resolution = new Resolution();
resolution
    .addr('ryan.crypto', 'ETH')
    .then((receiverETHAddress) => {
        // receiverETHAddress consists receiver ethereum address
        // use this address as recipient of the payment
    })
    .catch(console.error);
```
{% endtab %}

{% tab title="resolution-java" %}
```java
import com.unstoppabledomains.resolution.Resolution
...
DomainResolution resolution = new Resolution();
String receiverETHAddress = resolution.getAddress("ryan.crypto", "ETH");
// receiverETHAddress consists receiver ethereum address
// use this address as recipient of the payment
```
{% endtab %}

{% tab title="resolution-swift" %}
```swift
import UnstoppableDomainsResolution

guard let resolution = try? Resolution() else {
  print ("Init of Resolution instance with default parameters failed...")
  return
}

resolution.addr(domain: "ryan.crypto", ticker: "ETH") { result in
  switch result {
  case .success(let returnValue):
    let receiverETHAddress = returnValue
    // receiverETHAddress consists receiver ethereum address
    // use this address as recipient of the payment
  case .failure(let error):
    print("Expected eth Address, but got \(error)")
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Our libraries use Infura to interact with the Ethereum blockchain by default. To configure a custom Ethereum provider see our [Library configuration guide.](resolution-libraries/library-configuration.md)
{% endhint %}

**Records involved**

In the code above, the `addr()` and `getAddr()` methods convert the provided 3-letter ticker into the format `crypto.<TICKER>.address`. In this example, `ETH` ticker becomes `crypto.ETH.address`. The library uses `crypto.ETH.address` and the domain name to query the blockchain.

#### Example: Resolve `udtestdev-usdt.crypto` into USDT-ERC20 address

The `USDT` currency exists on multiple blockchains. Our libraries provide a dedicated method to look up cryptocurrency addresses for different blockchains.

{% tabs %}
{% tab title="resolution" %}
```javascript
const {default: Resolution} = require('@unstoppabledomains/resolution');
const resolution = new Resolution();
resolution
    .multiChainAddr('udtestdev-usdt.crypto', 'USDT', 'ERC20')
    .then((receiverUSDTAddress) => {
        // receiverUSDTAddress consists address for receiving USDT on Ethereum (ERC20 version)
        // use this address as recipient of the payment
    })
    .catch(console.error);
```
{% endtab %}

{% tab title="resolution-java" %}
```java
import com.unstoppabledomains.resolution.Resolution
...
DomainResolution resolution = new Resolution();
String receiverUSDTAddress = resolution.getMultiChainAddress("udtestdev-usdt.crypto", "USDT", "ERC20");
// receiverUSDTAddress consists address for receiving USDT on Ethereum (ERC20 version)
// use this address as recipient of the payment
```
{% endtab %}

{% tab title="resolution-swift" %}
```swift
import UnstoppableDomainsResolution

guard let resolution = try? Resolution() else {
  print ("Init of Resolution instance with default parameters failed...")
  return
}

resolution.multiChainAddress(domain: "udtestdev-usdt.crypto", ticker: "USDT", chain: "ERC20") { (result) in
  switch result {
  case .success(let returnValue):
     receiverUSDTAddress = returnValue;
     // receiverUSDTAddress consists address for receiving USDT on Ethereum (ERC20 version)
     // use this address as recipient of the payment
  case .failure(let error):
     print("Expected USDT-ETC20 Address, but got \(error)")
  }
}
```
{% endtab %}
{% endtabs %}

**Records involved**

The `multiChainAddress()` and `getMultiChainAddress()` methods create a key from the provided `USDT` ticker and `ERC20` version. The key format is `crypto.USDT.version.<VERSION>.address`. In the example above with the `ERC-20` version of `USDT`, the created key would be `crypto.USDT.version.ERC20.address`.

{% hint style="info" %}
See [Managing domain records](../allow-my-users-to-manage-existing-domains/managing-domain-records.md) for information about supported crypto payment tickers and USDT versions.
{% endhint %}

### Error handling

![Error example](../.gitbook/assets/errors-example.gif)

#### Common error cases to handle:

* Domain is not registered
* Crypto record is not found \(or empty\)
* Domain is not configured \(empty resolver\)
* Domain is not supported

{% tabs %}
{% tab title="resolution" %}
```javascript
const {default: Resolution} = require('@unstoppabledomains/resolution');
const resolution = new Resolution();
resolution
    .addr('domain-with-error.crypto', 'ETH')
    .then((ethAddress) => {
    })
    .catch((error) => {
        if (error.code === 'UnregisteredDomain') {
            console.log('Domain is not registered')
        }
        if (error.code === 'RecordNotFound') {
            console.log('Crypto record is not found (or empty)')
        }
        if (error.code === 'UnspecifiedResolver') {
            console.log('Domain is not configured (empty resolver)')
        }
        if (error.code === 'UnsupportedDomain') {
            console.log('Domain is not supported')
        }
    });
```

{% hint style="info" %}
To see all supported error codes please check [resolution library api docs](https://unstoppabledomains.github.io/resolution/v1.17.0/enums/resolutionerrorcode.html)
{% endhint %}
{% endtab %}

{% tab title="resolution-java" %}
```java
import com.unstoppabledomains.resolution.Resolution
import com.unstoppabledomains.exceptions.ns.NamingServiceException
import com.unstoppabledomains.exceptions.ns.NSExceptionCode

...
DomainResolution resolution = new Resolution();
try {
    String receiverETHAddress = resolution.getAddress("domain-with-error.crypto", "ETH");
} catch (NamingServiceException exception) {
   if (exception.getCode() == NSExceptionCode.UnregisteredDomain) {
        // Domain is not registered
   }
   if (exception.getCode() == NSExceptionCode.RecordNotFound) {
        // Crypto record is not found (or empty)
   }
   if (exception.getCode() == NSExceptionCode.UnspecifiedResolver) {
        // Domain is not configured (empty resolver)
   }
   if (exception.getCode() == NSExceptionCode.UnsupportedDomain) {
        // Domain is not supported
   }
}
```

{% hint style="info" %}
To see all supported error codes please check [resolution-java readme](https://github.com/unstoppabledomains/resolution-java#errors)
{% endhint %}
{% endtab %}

{% tab title="resolution-swift" %}
```swift
import UnstoppableDomainsResolution

guard let resolution = try? Resolution() else {
  print ("Init of Resolution instance with default parameters failed...")
  return
}

resolution.addr(domain: "domain-with-error.crypto", ticker: "ETH") { result in
  switch result {
      case .success(let returnValue):
        // Success flow
      case .failure(let error):
            switch error {
                case ResolutionError.unregisteredDomain:
                    // Domain is not registered
                    break;

                case ResolutionError.recordNotFound:
                    // Crypto record is not found (or empty)
                    break;

                case ResolutionError.unspecifiedResolver:
                    // Domain is not configured (empty resolver)
                    break;

                case ResolutionError.unsupportedDomain:
                    // Domain is not supported
                    break;
            }
  }
}
```

{% hint style="info" %}
To see all supported error codes please check [resolution-swift readme](https://github.com/unstoppabledomains/resolution-swift#possible-errors)
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Always check address validity after receiving a result from the library. The user has full control over the domain and is able to set any value - even values which are invalid.
{% endhint %}

## Domain Resolution using Resolution Service

Resolution service provides an API for getting domain data and metadata regardless of that domain's location \(whether it is stored in Ethereum, Zilliqa, or any other blockchain or further scaling solutions\). The service is used to cache blockchain events in a database for easy retrieval without accessing blockchain APIs.

The Github [Resolution Service Repository](https://github.com/unstoppabledomains/resolution-service)  includes a comprehensive README on how to install and run the Resolution Service on your own server.

The following diagram shows the interactions between nodes for Resolution Service.

![Node interactions in Unstoppable Domains&apos; Resolution Service](../.gitbook/assets/resolution-service.png)

### API Endpoints

For more information about the Resolution Service endpoints, see the [Resolution Service API Specification](http://resolve.unstoppabledomains.com/api-docs/). The specification uses OpenAPI format, which provides an interactive API explorer in which you can try out sample API calls. 

There are four endpoints in the Resolution Service API:

* `GET` domains: gets the list of domains
* `GET` domains/domainName: gets the resolution of the specified domain
* `GET` status: gets the synchronization status
* `GET` api-docs: returns a Swagger documentation page

### Resolution Service API Key

To ensure a high quality of service for API users, the Resolution Service includes an API key. Developers can request access to the API Key by doing the following:

* Email [legal@unstoppabledomains.com](mailto:legal@unstoppabledomains.com) with the request 
* Receive a terms of service for using the Resolution Service in the same email
* Terms of service must be accepted to access an API Key
* Post signing off on the Terms of Service, Unstoppable Domains will send you the API key to use the service

### Support

For assistance with this API Specification, please join our[ Discord channel](https://discord.gg/b6ZVxSZ9Hn) for real-time support from UD and the community.

## Integration Best Practices

* Always display the resolved address near the domain name for additional security.
* Don’t overwrite the input field with the cryptocurrency address.
* Always try to resolve a domain with the provided currency code.
* Always handle resolution errors according to error type.

![Best practices](../.gitbook/assets/best-practices.png)

## Resources

* [Get a test domain](../get-test-domain.md)
* [JavaScript Resolution library](https://github.com/unstoppabledomains/resolution)
* [Java Resolution library](https://github.com/unstoppabledomains/resolution-java)
* [Swift Resolution library](https://github.com/unstoppabledomains/resolution-swift)  
* [Unstoppable Domains Developer Community](https://discord.com/invite/b6ZVxSZ9Hn) Ask questions here!

