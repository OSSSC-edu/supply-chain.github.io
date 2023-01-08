---
layout: default
title: Public Key Inftastructure
parent: Security
nav_order: 1
description: "This chapter describes basic notions of the Public Key Infrastructure and key management"
---

# Public Key Infrastructure

### _Outline_ 📋
In this chapter, we learn about
- The concepts of [Public Key Infrastructure](#public-key-infrastructure)
- The use of [Public Key Encryption](#public-key-encryption)
- Basics in the [Handling of credentials](#credential-handling)


We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in the [references](#references).

## Public Key Infrastructure

Before delving into the finer details of securing the code infrastructure, we need to first discuss one of the basic components of access control and code attestation. The Public Key Infrastructure, or [PKI](https://en.wikipedia.org/wiki/Public_key_infrastructure), is a set of entities, with distinct roles, responsible for managing digital certificates. This includes their generation, storage, distribution, and revocation. These certificates can then be used to authenticate a user, or a machine, to a service.

The following is a simple illustration of the role of the PKI. The goal is to tie the keys used to encrypt the transmitted data to the sender and the receiver.

![](./img/PKI1.png) | 
*Image source: https://www.technologyies.com/what-is-pki-infrastructure-and-how-does-it-work/* | 

 <!-- ![](./img/PKI1.png) -->

The PKI ensures that the `public` keys used to communicate with a server, a company, or an individual, belong to the actual owner. As long as the certificate authority is trusted, a user can be sure that the communication happens with the intended recipient.

To bring it to the context of supply chains: The PKI helps ensure that the downloaded software was produced by a specific entity; it can also ensure that the code has not been changed during the lifetime of the supply chain (if signing/verification happens at each step). Moreover, the PKI can also be used to trace published code to a specific individual. We can see in the following picture the need for an infrastructure that takes care of authentication. In the real world, the driver would provide an ID to the factory and the store. In the software supply chain, this is accomplished with the use of credentials.

 ![](./img/supply-chain.png) |
 *Image source: https://www.docker.com/blog/* |

### Public Key Encryption

The PKI also facilitates the use of assymetric encryption, known also as public key encryption (PKE). In this scheme, each user has two distinct keys; one is `public`, while the other must always remain `private`. The public key can be freely distributed to the world and is required to `verify` that a piece of software was `signed` (or encrypted) by the corresponding private key. This highlights the importance of keeping the private key secure; leaking this key would allow anyone to impersonate its actual holder.

In the context of code infrastructure security, a compromised `private` key would allow anyone to `push` to a specific branch, `sign` the code such that it appears to originate from someone else, such as [Linus Torvalds](https://github.com/torvalds), and ultimately introduce malicious code into the supply chain.


### Credential Handling

Due to its nature, improper handling of credentials can lead to serious damage, especially since credentials ensure the security and integrity of a supply chain. The following steps are recommended for propoer management of credentials:
- Private keys must always remain secret
- When possible, two-factor authentication, or 2FA, should be used
- Keys and credentials should be changed in periodically, and should not be permanent
- Certificates should have an expiration date
- Keys should be used for one protocol only; this prevents cross-protocol attacks, e.g., [SSL attack](https://www.controlcase.com/cross-protocol-attack-on-tls-using-sslv2-drown-vulnerability-cve-2016-0800-mar-2016/))


## DIY

### _Novice_ 👾
- Create a new GitHub repository
- Perform the following functions: clone, commit, merge, push, pull request
- Create access `SSH` keys and assign them to your GitHub account
- Create signing `SSH` or `gpg` keys and attach them to your GitHub account
- Sign a commit

### _Expert_ 💯
- Configure branch rules for your repository on GitHub to restrict access
- Set up and enable 2FA functionality in your GitHub account

<!-- ## Industry Use Cases
    The following lists outline the general knowledge that a user should have from a security perspective.
## Test Questions / Areas / Learning Goal
- Understand the difference between using HTTPS and SSH for accessing the repository
- Understand how to store and manage credentials
- What problems can static and binary analysis solve
- Has the capability to argue about properties of the cryptographic keys, e.g., the size and the cipher used
- Understands the implications and potential vulnerabilities that emerge from the choice of key properties, and storage, and 2FA options
- What type of analysis to use and when
- What guarantees does static and binary analysis provide
-->

## References

1. [How PKI works](https://www.thesslstore.com/blog/how-pki-works/)
2. [What is PKI](https://www.technologyies.com/what-is-pki-infrastructure-and-how-does-it-work/)


<!-- [hide email](https://stackoverflow.com/questions/43863522/error-your-push-would-publish-a-private-email-address) -->
<!-- (KK, PP)
     - open question: different users with different repos - 
        - is there a connection? 
        - can I convince you? 
        - What infrastructure is needed? 
        - What if I loose the keys? Someone has my password and introduces his own keys?
     -(KK,PP)

-->