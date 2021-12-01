---
description: This page details the scopes currently supported by Login with Unstoppable.
---

# Scopes

Scopes are used to control access to user's data and includes specific information that the user is willing to share with the dApp (e.g., I own this wallet address; I own this email address). Rather than granting complete access to a user’s account, scopes give apps a way to request a more limited scope of what they are allowed to do with user data, and users are more willing to authorize an application if they know exactly what the application can and cannot do with their personal information. &#x20;

Login with Unstoppable is built utilizing existing standards, specifically [OpenID Connect](https://auth0.com/docs/authorization/protocols/openid-connect-protocol). The goal of the protocol is to link a domain to an OpenID Provider that can be used to authenticate end-users. The [OpenID scope](https://auth0.com/docs/configure/apis/scopes/openid-connect-scopes) must be included in addition to any other scope supported by Login with Unstoppable.

Login with Unstoppable supports the following scopes which are detailed below:&#x20;

* [OpenID scope](scopes.md#openid-scope) (required)
* [wallet scope](scopes.md#wallet-scope)
* [email scope](scopes.md#email-scope)
* [email:optional scope](scopes.md#email-optional-scope)

## OpenID Scope

Login with Unstoppable uses OpenID Scope to authenticate and authorize access to the user's personal data, such as wallet and email address. The scopes requested by an application varies depending on the type of user data needed by the application. The scopes requested by the application will be presented to the user in a list.

![Example scope list presented to UD users](../.gitbook/assets/consent-screen-marked.png)

Each scope returns a set of user attributes, which are called claims. Once the user authorizes the requested scopes, the claims are returned in an ID Token.

{% hint style="info" %}
This is a required scope for using Login with Unstoppable. The [OpenID scope](https://auth0.com/docs/configure/apis/scopes/openid-connect-scopes) must be included in addition to any other scope used to integrate this feature.
{% endhint %}

## Wallet Scope

The Login with Unstoppable wallet scope is best used for retrieving metadata about the user’s wallet. It returns two custom claims:

1. wallet\_address - The address associated with the domain.
2. wallet\_type\_hint - A string indicating the type of wallet associated with the domain with two possible values:

* injected - A web3/browser-based wallet like [MetaMask](https://docs.metamask.io/guide/)
* walletconnect - Using the [WalletConnect](https://walletconnect.org) protocol

## Email Scope

The Login with Unstoppable email scope can be used to retrieving metadata about the user's preferred email address. It is based on the [OIDC Standard email scope](https://openid.net/specs/openid-connect-basic-1\_0.html#Scopes).

Scope values:

* openid
* wallet&#x20;
* email

## Email Optional Scope

The Login with Unstoppable **email:optional** scope is used to retrieve metadata about the user's preference for sharing their email address. Users will be able to select or deselect this option in the UI presented to them.

Scope values:

* openid
* wallet&#x20;
* email
* email:optional

![UI for email:optional scope](../.gitbook/assets/email\_optional\_scope-small.jpg)
