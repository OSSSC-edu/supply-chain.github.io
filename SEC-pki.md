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
- The use of [Public Key Cryptography](#public-key-encryption)
- The concepts of [Public Key Infrastructure](#public-key-infrastructure)
- Some basic, but important, steps for [Handling credentials](#credential-handling)


We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in the [references](#references).

## Public Key Cryptography

In public key cryptography, every user or system utilizes a pair of keys; called `public` and `private` keys.
While the `public` key can be freely distributed to the world, e.g., posted on a website or send through a messaging service, the corresponding `private` key must remain secret. By using these pair of keys the following
are possible:

- Some piece of data can be encrypted using the `public` key of someone else. This guarantees that only the person
holding the corresponding `private` key can decrypt it. This guarantees the *confidentiality* of the information.
- Encrypting, or better yet `signing` some piece of data with the `private` key means that everyone in possession
of the corresponding `public` key can decrypt (or `verify`) the information. This, does not provide confidentiality, but provides non-repudiation, i.e., we can claim that the data came from someone in possession of the secret key. Forgery in this case is not possible. 
  
The second bullet highlights the importance of keeping the private key secure; leaking this key would allow anyone to impersonate its actual holder. This becomes even more critical when we consider the usecases of public key cryptography:

- Use in [SSH](https://en.wikipedia.org/wiki/Secure_Shell), for establishing secure tunnels to remote machines; used in [Transport Layer Security (TLS)](https://en.wikipedia.org/wiki/Transport_Layer_Security) that provides communication security in computer networks (including HTTPS).
- Usa in messaging services such signal, telegram, whatsapp and many more.
- Algorithms of this nature also help in key distribution (e.g., the [Diffie-Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) exchange) and other notable systems such as [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)), which are used daily by almost everyone in the world.

In the context of code infrastructure security, a compromised `private` key would allow anyone to `push` to a specific branch, `sign` the code such that it appears to originate from someone else, such as [Linus Torvalds](https://github.com/torvalds); thus, hiding potential malicious code. Similarily, an update for one of the packages in our supply chain can be the point of entry for malicious code. If the `private` key of the package provider is compromised, the update will be downloaded and incorporated automatically. In both cases, malicious code is introduced into the supply chain due to the inherent trust to the user and the cryptosystem.


## Public Key Infrastructure

However, simply using a pair of keys to encrypt/decrypt and sign/verify some piece of data does not guarantee that the information came from a specific user. Ultimately, a pair of keys is not tied to a person or a system. To solve this problem, an infrastructure is required in order to bind these two aspects together. Public Key Infrastructure, or [PKI](https://en.wikipedia.org/wiki/Public_key_infrastructure), is a set of entities, with distinct roles, responsible for managing digital certificates. This includes their generation, storage, distribution, and revocation. These certificates can then be used to authenticate a user, or a machine, to a service. Simply, a user can provide his `public` key to a [Certificate Authority (CA)](https://en.wikipedia.org/wiki/Certificate_authority), prove his identity to that authority, e.g., by physically going to an office, which will then create a certificate containing the identity of the user and the `public` key. This, guarantees that the `public` key (or certificate) distributed to the web is bound to a specific person or system.

The following is a simple illustration of the role of the PKI when sending an email to a third-party. The user needs to register to an authority; a certificate is created out of the `public` key; the email is signed using the `private` key and send to a third party; the third party can use the public certificate to `verify` that the sender corresponds to the correct entity.

![](./img/PKI1.png) | 
*Image source: https://www.technologyies.com/what-is-pki-infrastructure-and-how-does-it-work/* | 

 <!-- ![](./img/PKI1.png) -->

As long as the certificate authority is trusted by all parties, a user can be sure that the communication happens with the intended recipient.

To bring it to the context of supply chains: The PKI helps ensure that the downloaded software was produced by a specific entity; it can also ensure that the code has not been changed during the lifetime of the supply chain (if signing/verification happens at each step). Moreover, the PKI can also be used to trace published code to a specific individual. We can see in the following picture the need for an infrastructure that takes care of authentication. In the real world, the driver would provide an ID to the factory and the store. In the software supply chain, this is accomplished with the use of credentials.

 ![](./img/supply-chain.png) |
 *Image source: https://www.docker.com/blog/* |

### Credential Handling

Due to its nature, improper handling of credentials can lead to serious damage, especially since credentials ensure the security and integrity of a supply chain. The following steps are recommended for proper management of credentials:
- Private keys must always remain secret. Losing this key, allows anyone to impersonate us!
- When possible, [multi-factor authentication](https://en.wikipedia.org/wiki/Multi-factor_authentication) should be used when accessing systems. This ensures that even with compromised keys, access to the system is protected.
- Keys and credentials should be changed periodically, and should not be permanent. A compromised key can only be used for as long as it is valid.
- Certificates should have an expiration date.
- Keys should be used for one protocol and functionality only; this prevents cross-protocol attacks, e.g., [SSL attack](https://www.controlcase.com/cross-protocol-attack-on-tls-using-sslv2-drown-vulnerability-cve-2016-0800-mar-2016/)).


## DIY

### _Novice_ 👾
- Create a pair of public and private keys, e.g, by using `gpg`.
- Encrypt a message using the `public` key and decrypt it using the `private` key.
- Can someone else read the message?
- Why do we need Certificate Authorities?
- What is inherently needed for the PKI to function for everyone?

### _Expert_ 💯
- Create two pair of keys for two users Alice and Bob
- As Alice, encrypt some data using her `private` key and then encrypt the result using the `public` key of Bob.
- Try to reverse the procedure as Bob; what is the order of operation?
- What does these two operations guarantee (from the perspective of Bob)?

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

1. [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)
2. [SSH](https://en.wikipedia.org/wiki/Secure_Shell)
3. [Diffie-Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)
4. [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem))
5. [How PKI works](https://www.thesslstore.com/blog/how-pki-works/)
6. [What is PKI](https://www.technologyies.com/what-is-pki-infrastructure-and-how-does-it-work/)
7. [Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority)


<!-- [hide email](https://stackoverflow.com/questions/43863522/error-your-push-would-publish-a-private-email-address) -->
<!-- (KK, PP)
     - open question: different users with different repos - 
        - is there a connection? 
        - can I convince you? 
        - What infrastructure is needed? 
        - What if I loose the keys? Someone has my password and introduces his own keys?
     -(KK,PP)

-->