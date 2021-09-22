---
description: >-
  This page provides a high-level overview of the Login with Unstoppable
  feature.
---

# High Level Overview

Login with Unstoppable allows an Unstoppable Domain owner to log in and share information with applications. This allows application developers to learn information about their users (email, for example) without needing to host or maintain their own CRM database. With current wallet-based sign-in methods it is difficult or impossible for application developers to contact their users. They simply don't have an email address for proactive communication. Instead, app developers have to rely on passive communication methods such as Twitter and Discord to share important announcements. This is worse for users, worse for developers, and worse for web3.

Login with Unstoppable gives users and apps a simple way to solve this problem. This protocol extends the standard OpenID Connect \(OIDC\) authorization protocol with a simple wallet signature. After authentication, users have the ability to pass along relevant metadata such as email addresses, social profiles, community memberships, etc. with their login. Applications can request information but the decision of what to share is 100% user-controlled. This decentralized authorization process enables a better user experience and a closer relationship between applications and the communities they serve.

![User flow for Unstoppable Logins feature](../.gitbook/assets/unstoppable-logins-user-flow.png)

## Benefits for dApps

1. Communicate with community members directly via permissioned access to their email addresses.
2. Avoid hosting a database of user contact information by asking for permissions to access contact information only when it's needed.
3. dApps will be web3 compliant.

## Benefits for Users 

1. Users can choose to share what information \(if any\) they want to share with an application. The information sharing is 100% opt-in and wholly controlled by the user.
2. No need to remember multiple unique usernames and passwords. One login for every web3 application.
3. Gives users absolute control over their login credentials, not a corporation.

## Limitations

* Does not support .zil domains
* Pre-made components are only available initially in React
