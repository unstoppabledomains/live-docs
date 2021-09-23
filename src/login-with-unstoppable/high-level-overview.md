---
description: >-
  This page provides a high-level overview of the Login with Unstoppable
  feature.
---

# High Level Overview

Login with Unstoppable allows an Unstoppable Domain owner to log in and share information with applications. This allows application developers to learn information about their users \(email, for example\) without needing to host or maintain their own CRM database. With current wallet-based sign-in methods it is difficult or impossible for application developers to contact their users. They simply don't have an email address for proactive communication. Instead, app developers have to rely on passive communication methods such as Twitter and Discord to share important announcements. This is not ideal for users, developers, or the future of web3.

Login with Unstoppable gives users and apps a simple way to solve this problem. This protocol extends the standard OpenID Connect \(OIDC\) authorization protocol with a simple wallet signature. After authentication, users have the ability to pass along relevant metadata such as email addresses, social profiles, community memberships, etc. with their login. Applications can request information but the decision of what to share is 100% user-controlled. This decentralized authorization process enables a better user experience and a closer relationship between applications and the communities they serve.

## Benefits for Decentralized Applications \(dApps\)

1. Communicate with community members directly via opt-in access to their email addresses.
2. Avoid hosting a database of user contact information by asking for permissions to access that information only when it's needed.

## Benefits for Users

1. Information sharing is 100% opt-in.
2. Only one login for every web3 application. No need to remember multiple unique usernames and passwords. 
3. Gives users absolute control over their login credentials \(private key\), not a corporation.

## Limitations

* Does not support .zil domains
* Pre-made components are only available initially in React. The modal is written in react, which has a larger library size.

