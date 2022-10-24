---



layout: default
title: Security in code infrastructure
nav_order: 5
description: ""
permalink: /security
---

# Security in code infrastructure

## Public Key infrastructure
Before delving into the finer details of securing the code infrastructure, we need to first discuss one of the basics components of access control and code attestation, among other things. Public Key Infrastructure (PKI) is a set of entities, with distinct roles, responsible for 
managing digital certificates; this includes, their generation, storage, distribution and most importantly revocation.

The following is a schematic of the PKI when a webpage needs to be accessed from the user's browser:

 ![](https://www.thesslstore.com/blog/wp-content/uploads/2020/07/how-pki-works-overview.png)|
|:--:|
| *Image source: https://www.thesslstore.com/blog/how-pki-works/*

PKI ensures that the public keys used to communicate with a server, a company, or an individual, belongs to the actual owner. As long as the certificate authority is trusted, a user can be sure that the communication happens with the intended recipient. To bring it to the context of supply chains: PKI helps ensure that the downloaded software was produced by a specific entity; it can ensure that the code has not been changed during the lifetime of the supply chain; it can also be used to connect published code to a specific individual.  

### Public Key Encryption
The PKI also facilitates the use of assymetric encryption, known also as public key encryption (PKE). In this scheme, each user has two distinct keys; one is public, the other must always remain private. The public key can be freely distributed to the world and is required to `verify` that a piece of software was `signed` (or encrypted) by the corresponding private key. This, highlights the importance of keeping the private key secure; leaking this key would allow anyone to impersonate its actual holder. 

In the context of code infrastructure security, a compromised private key would allow anyone to `push` to a specific branch, `sign` the code to appear to originate from someone else, e.g., Linus Torvald, and ultimately introduce malicious code into the supply chain.

## Static analysis
`TODO: add static analysis`
## Binary analysis
`TODO: add binary analysis`

## Beginner, Normal, Expert Level
## Industry Use Cases
## Test Questions / Areas / Learning Goal
## References

