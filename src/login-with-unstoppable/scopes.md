---
description: This page details the scopes currently supported by Login with Unstoppable.
---

# Scopes

Scopes refers to information that the user will share with the dApp (e.g., I own this wallet address; I own this email address). Login with Unstoppable currently supports three scopes: wallet, email, and email:optional.

## Wallet Scope

The Login with Unstoppable wallet scope is best used for retrieving metadata about the user’s wallet. It returns two custom claims:

1. wallet\_address - The address associated with the domain.
2. wallet\_type\_hint - A string indicating the type of wallet associated with the domain with two possible values:

* injected - A web3/browser-based wallet like [MetaMask](https://docs.metamask.io/guide/)
* walletconnect - Using the [WalletConnect](https://walletconnect.org) protocol

## Email Scope

The Login with Unstoppable email scope can be used to retrieving metadata about the user's preferred email address. It is based on the [OIDC Standard email scope](https://openid.net/specs/openid-connect-basic-1\_0.html#Scopes).

## Email Optional Scope

The Login with Unstoppable **email:optional** scope is used to retrieve metadata about the user's preference for sharing their email address. Users will be able to select or deselect this option in the UI presented to them.

![UI for email:optional scope](<../.gitbook/assets/email\_optional\_scope (1).png>)
