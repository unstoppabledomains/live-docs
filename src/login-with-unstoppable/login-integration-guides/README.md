---
description: >-
  This page reviews the integration guides for Login with Unstoppable. This
  feature works for Polygon and Ethereum domains.
---

# Login Integration Guides

Login with Unstoppable is a versatile feature with several integration pathways available for developers. This page reviews the integration guides, overall features, and related libraries for each installation option.

## Step 1: Get Login Credentials

Before beginning the integration process for Login with Unstoppable, you must obtain client credentials and configure your application. Please see the [Getting Login Credentials Guide](../getting-login-credentials.md) for more details.

## Step 2: Choose Your Integration Path

There are several ways to integrate with Login with Unstoppable, which is detailed in the chart below.

| Short Description                          | Pathway or Features                                                                                                                   | Integration Guides                                                                                                                                                                                                                                        |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No Ethereum Provider with Popup Feature    | generic @uauth/js integration, no ethereum provider, with callback, with popup feature                                                | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="login-with-popup.md">Login with Unstoppable Guide with Popup</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol>       |
| No Ethereum Provider with Popup Feature    | generic @uauth/js integration, no ethereum provider, with callback, no popup feature                                                  | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="login-without-popup.md">Login with Unstoppable Guide without Popup</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol> |
| Ethereum Provider with Web3 React Library  | custom @uauth/js integration, with ethereum provider, web3-react library                                                              | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="web3-react-guide.md">Web3 React Guide</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol>                              |
| Ethereum Provider with Web3 Modal Library  | custom @uauth/js integration, with ethereum provider, web3modal library                                                               | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="web3-modal-guide.md">Web3 Modal Guide</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol>                              |
| Ethereum Provider with BNC Onboard Library | custom @uauth/js integration, with ethereum provider, bnc-onboard library                                                             | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="bnc-onboard-guide.md">BNC Onboard Guide</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol>                            |
| Custom uAuth Node without Frontend UI      | custom @uauth/node integration for server-side applications, without frontend UI, DOM UI package recommended to help with frontend UI | <ol><li><a href="../getting-login-credentials.md">Getting Login Credentials</a></li><li><a href="node-js-server-guide.md">Node.js Server Guide</a></li><li><a href="../login-ui-requirements.md">Login UI Requirements</a></li></ol>                      |

{% hint style="info" %}
The [UAuth Demo Application](https://uauth-demo.uc.r.appspot.com) is available for developer use along with a [single page sample application](https://github.com/unstoppabledomains/uauth/tree/main/examples/spa/src) to model the flow. Applications can also use Unstoppable Domain’s [UAuth Library](https://github.com/unstoppabledomains/uauth) to simplify the integration.&#x20;
{% endhint %}

## Resources

For assistance with the Login with Unstoppable feature, please join our [Discord channel](https://discord.gg/b6ZVxSZ9Hn) for real-time support from UD and the community.
