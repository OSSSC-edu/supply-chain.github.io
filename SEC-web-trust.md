---
layout: default
title: Web of Trust
parent: Security
nav_order: 2
description: "This chapter describes the web of trust and how key-pairs can be used without the use of an infrastructure"
---

# Web of Trust

### _Outline_ 📋
In this chapter, we learn about
- What is the [Web of Trust](#web-of-trust)
- What are the [Basic Differences to PKI](#basic-differences-to-pki)
- How can we [Enter the World of Trust using GPG](#entering-the-world-of-trust-using-gpg)
  
We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in the [references](#references).


## Web of Trust

In the previous section, we utilized the PKI to bind public keys to a physical entity. However, PKI is not the only option; attesting code and infrastructure can be done in another way. Following the same procedure as before: a user can distribute their public key and sign their code/work with a private key. The public key can then be used to verify that the code was submitted by the user, through their corresponding private key. The alternative to PKI, is the web of trust. The web of trust is a *decentralized* model that allows each user to endorse the association between a public key and a person; this way indirect trust can be achieved. The following image illustrates this:

![](./img/Web_of_Trust.png) |
*Image source: https://en.wikipedia.org/wiki/Web_of_trust* |

## Basic differences to PKI

Instead of requiring a central authority to sign the user's `public` key (thus creating the certificate), the users take up the role of the Certificate Authority (CA). Because, several endorsements for a specific key needs to happen for it to be trusted (for openPGP-compliant implementations), web of trust avoids the single point of failure that exists in the PKI system; compromising a single CA would allow for the creation of trusted keys in the whole domain under this CA (including other CAs). On the other hand, it may be difficult for new users to find endorsements for their (self-signed) certificates and ultimately be able to comminicate, e.g., because they cannot physically meat other users.

## Entering the world of trust using GPG

Our keys need to be trusted by other entities in the web of trust; a task not trivial or without pitfalls. After we have generated a key (`gpg --gen-key`), we need to start distributing our key to remote parties.
- We can see all the keys in our keyring by running: `gpg --list-keys`.
- To export a key, gpg allows to do `gpg --export <id>`; when we want to email this key we can also add the option `--armor` to output the key in ASCII-armored format.
- When we receive a `public` key from someone else, we need to perform a few actions:
  - `gpg --fingerprint <key>` will give us all the information for the provided key
  - `gpg --import <key>` will import a key into our keyring
- So far, we have not trusted any key in our keyring. When we want to endorse a key because we know it comes from a specific person we execute: `gpg --lsign-key <key>`. 
- In case we want to check the signature of a key we can perform: `gpg --check-sig <key>`. This command gives us some very usefull insights:
  - We can see the number of endorsments the key has!
  - We can see in the form of `!` or `-` if the key is verified or not respectively


## DIY

### _Novice_ 👾
- Generate a key pair and send your `public` key to a friend - or create two pairs in the same machine
- Import a key to your keyring
- Why do we need to check the fingerprint of a key before importing it?
- What happens when we endorse a key? How does this operation confers trust?

### _Expert_ 💯
- 


## References
