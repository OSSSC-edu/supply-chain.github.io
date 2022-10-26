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

 ![](./figures/how-pki-works-overview.png)|
|:--:|
| *Image source: https://www.thesslstore.com/blog/how-pki-works/*

PKI ensures that the `public` keys used to communicate with a server, a company, or an individual, belongs to the actual owner. As long as the certificate authority is trusted, a user can be sure that the communication happens with the intended recipient. To bring it to the context of supply chains: PKI helps ensure that the downloaded software was produced by a specific entity; it can also ensure that the code has not been changed during the lifetime of the supply chain (if signing/verification happens at each step); it can also be used to connect published code to a specific individual.  

### Public Key Encryption
The PKI also facilitates the use of assymetric encryption, known also as public key encryption (PKE). In this scheme, each user has two distinct keys; one is `public`, the other must always remain `private`. The public key can be freely distributed to the world and is required to `verify` that a piece of software was `signed` (or encrypted) by the corresponding private key. This, highlights the importance of keeping the private key secure; leaking this key would allow anyone to impersonate its actual holder. 

In the context of code infrastructure security, a compromised `private` key would allow anyone to `push` to a specific branch, `sign` the code to appear to originate from someone else, e.g., Linus Torvald, and ultimately introduce malicious code into the supply chain.

## Static analysis
`TODO: add static analysis`
## Binary analysis
`TODO: add binary analysis`
## Access control - 2FA - on the repo
In a typical sense, `git` does not provide access control; git after all is a source-code management tool. A repository can be private or public but the repositories themselves do not implement any authentication. This can be tackled with other solutions: some [examples](https://wincent.com/wiki/Git_repository_access_control) of this include the use of `git-daemon` to provide read-only (anonymous) access and the requirement of using SSH keys to `push`; users without the appropriate SSH key cannot `push` to the repository.

However, a simple step for improving the security of a repository is to introduce Two-Factor Authentication (2FA) when logging-in into a git account. 2FA effectively requires the user to present two pieces of information to authenticate themselves (e.g., knowledge - a password, and possession - a phone that receives an one-time password). This raises the difficulty of compromising an account and gaining access to critical code. Github provides a detailed guide on how to configure [2FA](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication) and its [account-recovery](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication-recovery-methods). Accessing the account can be [straightforward](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/accessing-github-using-two-factor-authentication) through the web, or through the command line using [SSH](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github).

Apart from restricting access to the code base, github also provides protection rules that can be applied in order to restrict the possible actions, e.g., pull request, merge, etc. For example, it allows repository administrators to require pull requests for all branches that contain the word `release` in their name; or, that pull requests that affect other peoples' code must be first approved by the code owner. More information about this proccess can be found in  [branch protection rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)


### Commit signing

Another usefull service that `git` allows through the use of `SSH` keys, is the possibility to `sign` code that is `pushed` to a repository. This ensures that all commits are authenticated and the person responsible for the code can be attributed.

The following lines enable code signing from the command line ([instructions](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)) and assumes that `SSH` keys have already been created, e.g., for accessing the repository ([SSH key generation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent), [SSH access](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)) and the key is added as a `signing key` in the user's account.
```
git config commit.gpgsign true
git config gpg.format ssh //when using SSH key instead of GPG
git config user.signingkey "public_key"
```

More information on the proccess of signing commits can be found in the [signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits) section in github.


## Credential Management
We already touched upon it in the first section, but improper credential management is one of the leading causes of security compromises [citation]. 

The simplest steps for credential management can be summarized as:
- Private keys must always remain secret
- 

`TODO: alternative to web of trust`

### Web of Trust
PKI is not necessarily needed  for attesting code and infrastructure. A user can distribute its public key and sign his code/work with a private key. The public key can then be used to verify the owner of the relevant code/work. 

`TODO: web of trust specifics`


## Beginner, Normal, Expert Level
## Industry Use Cases
## Test Questions / Areas / Learning Goal
## References

1. [Static analysis for security. Brian Chess, Gary McGraw](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=1366126)
2. [Countering trusting trust through diverse double-compiling. David A. Wheeler, 2005.](https://ieeexplore.ieee.org/document/1565233)