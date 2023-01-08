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
- The [Web of Trust](#web-of-trust)
We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in the [references](#references).


## Web of Trust

PKI is not necessarily needed for attesting code and infrastructure. A user can distribute their public key and sign their code/work with a private key. The public key can then be used to verify that the code was submitted by the user, through their corresponding private key. This, however, does not link the public key with an individual; when PKI is not used, the alternative is to create a web of trust. The web of trust is a decentralized model, allowing each user to endorse the association between a public key and a person; this way indirect trust can be achieved. The following image illustrates this:

![](./img/Web_of_Trust.png) |
*Image source: https://en.wikipedia.org/wiki/Web_of_trust* |


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


## References
