---
description: >-
  This page covers the resolution service API feature for Unstoppable domains,
  which is hosted by Alchemy and Polygon.
---

# Resolution Service API

Resolution service provides an API for getting domain data and metadata regardless of that domain's location (whether it is stored in Ethereum, Zilliqa, or any other blockchain or further scaling solutions). The service is used to cache blockchain events in a database for easy retrieval without accessing blockchain APIs.

{% hint style="warning" %}
We no longer support ENS resolution, but developers can [integrate directly with ENS](https://docs.ens.domains/dapp-developer-guide/resolving-names) for continued support. Our API resolution service is hosted by Alchemy and Polygon as part of our [Layer 2 solution](../polygon-l2-network/polygon-high-level-overview.md).&#x20;
{% endhint %}

The Github [Resolution Service Repository](https://github.com/unstoppabledomains/resolution-service) includes a comprehensive README on how to install and run the Resolution Service on your own server.

The following diagram shows the interactions between nodes for Resolution Service.

![Node interactions in Unstoppable Domains' Resolution Service](../../.gitbook/assets/resolution-service.png)

## API Endpoints

For more information about the Resolution Service endpoints, see the [Resolution Service API Specification](http://resolve.unstoppabledomains.com/api-docs/). The specification uses OpenAPI format, which provides an interactive API explorer in which you can try out sample API calls.&#x20;

There are four endpoints in the Resolution Service API:

* **`GET`** domains: retrieves and displays the list of domains
* **`GET`** domains/{domainName}: gets the resolution of the specified domain
* **`GET`** status: gets the synchronization status
* **`GET`** metadata/{domainortoken}: retrieves the metadata for the domain or token

## Resolution Service API Key

To ensure a high quality of service for API users, the Resolution Service includes an API key. Developers can request access to the API Key by doing the following:

* Email [legal@unstoppabledomains.com](mailto:legal@unstoppabledomains.com) with the request&#x20;
* Receive a terms of service for using the Resolution Service in the same email
* Terms of service must be accepted to access an API Key
* Post signing off on the Terms of Service, Unstoppable Domains will send you the API key to use the service

## Support

For assistance with this API Specification, please join our[ Discord channel](https://discord.gg/b6ZVxSZ9Hn) for real-time support from UD and the community.
