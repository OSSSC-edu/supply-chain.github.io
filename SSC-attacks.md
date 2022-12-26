---
layout: default
title: OSS Supply Chain Attacks
parent: OSS Supply Chain
nav_order: 1
---

# OSS Supply Chain Attacks

An open-source software (OSS) [supply chain attack](https://en.wikipedia.org/wiki/Supply_chain_attack) is a type
of [cyberattack](https://en.wikipedia.org/wiki/Cyberattack) in which a malicious actor targets the supply chain of OSS of a software project.
The goal of the attacker is often to compromise proprietary software (e.g., company), and potentially exploit its users.
These attacks can occur at various points in the software supply chain of a project.
For example, during its development, distribution, or installation.

One common form of attack is to insert malicious code into the software directly during the development process.
This can be done by compromising a developer's computer, or by gaining access to the project's source code repository.
In this latter case, an attacker could modify the code without the knowledge of the other developers.
Once the malicious code is included, it can be triggered at a later time to execute the attacker's payload.

Another method of OSS supply chain attacks is to distribute a compromised version of a [software dependency](package-managers.md#software-dependencies) through
official and unofficial channels, such as through a [package manager](package-managers.md), a malicious website or via email.
The compromised dependency can then be installed by a user, and the malicious code will be executed every time the dependency is used.
This can be effective if the developers have not strict control over the software supply chain of dependencies in their applications, or when users are not
aware of the official distribution channels for their software application (e.g., when downloading an mobile app from a unsecure vendor).

Overall, OSS supply chain attacks can be difficult to detect and prevent.
This is because the open-source nature of the software makes it difficult to track the source of the malicious code.
Consequently, it is important for OSS projects to set up strong security measures to protect against these types of attacks.
For example, code reviews, secure development practices, and [reproducible builds](SSC-reproducible-builds.md), [integrity checks](SSC-integrity.md), and secure
deploying mechanisms within the CI/CD pipeline.
Users of OSS should also be vigilant and only download software from trusted sources.

# Example: The SolarWinds Supply Chain Attack

The SolarWinds attack was a major software supply chain attack that occurred in 2020.[^3]
It is a typical example of the fragility that permeates modern software supply chains.
It involved the compromise of the software supply chain of SolarWinds, a company that provides IT management software to government agencies and businesses
around the world.

A malicious actor gained access to the Orion monitoring and management system operated by the U.S. company SolarWinds and inserted malicious code into the
deployment infrastructure.
Interestingly, changes were done at the source code level, which means that code was tested, signed, and released through the SolarWinds platform, and nobody in
the company noticed the change.
The malicious code stayed dormant for two weeks.
After that, it mimicked another known protocol to exfiltrate users' credentials, which were used to craft security tokens, allowing attackers to access
confidential data.
The attackers inserted malicious code into a software update that was distributed to SolarWinds' customers.
When the customers installed the update, the malicious code was executed, allowing the attackers to gain access to the customers' networks and potentially
exfiltrate sensitive data.

The attack was discovered in December 2020, but it is believed to have started as early as March of that year.
The malicious code, which was dubbed "Sunburst" by cyber-security researchers, was designed to be stealthy
and [difficult to detect](https://www.csoonline.com/article/3601508/solarwinds-supply-chain-attack-explained-why-organizations-were-not-prepared.html).
It was able to bypass many security defenses and remained undetected for months.

It is believed to have affected thousands of organizations, including multiple government agencies in the United States.[^5]
The full extent of the damage caused by the attack is not yet known, but it is likely to be significant.
The attack has prompted a review of software supply chain security practices and has raised concerns about the potential for similar attacks in the future.
It is a reminder of the importance of secure software development and distribution practices, as well as the need for organizations to remain vigilant in
detecting and responding to cyber threats.

Incidents at this scale are evidence of the lack of awareness related to this issue and the lack of control of companies and the government regarding the
software products and services deployed to their clients.
Governments have been somewhat ineffectual in handling supply-chain issues.
Mass-scale software development and future global innovation are at risk if governments enforce more restrictive security gates to prevent incidents such as the
SolarWinds.
Technology-based solutions need to be developed in order to cope with the challenge of [securing the software supply chain](https://www.cesarsotovalero.net/blog/the-software-supply-chain.html).

# Attack Vectors in OSS Supply Chain Attacks

[//]: # (From my blog)

Today it is almost impossible to ship any large software solution fast without the help of third-party dependencies.
For almost every software company, relying on software that is not made in-house poses several risks.
[Software supply chain attacks](https://en.wikipedia.org/wiki/Supply_chain_attack) occur when a malicious actor penetrates the CI/CD chain to insert malicious
code.
If a single component in the supply chain gets compromised, then the whole infrastructure may be at the mercy of the attacker.
Supply chain attacks are very difficult to detect because the product continuously changes at each stage: from source code, to binaries, to an application that
runs somewhere in the cloud and is interacting with clients.
Attackers could target all the layers of the supply chain, from malicious plugins in IDEs to corrupted compilers.
However, they often focus on the less secure elements in the supply chain and heavily rely on the trust that make code reuse possible.
Attacks targeting third-party components are expected to become more prominent over the next few years.

> “Projects often incorporate code and libraries from many sources with unknown provenance...” ― <cite><a href="http://web.mit.edu/ha22286/www/">Hamed
> Okhravi</a></cite>

Package managers are particularly susceptible to supply chain attacks (
e.g., [typosquatting](https://news.ycombinator.com/item?id=11862217), [cryptojacking](https://www.kaspersky.com/resource-center/definitions/what-is-cryptojacking),
and malicious contributors).
This is due to the lack of efficient mechanisms for detecting malicious code injected into packages uploaded to popular package repositories.
For example, there is no security audit performed on the packages submitted `npm`, the largest repository of JavaScript libraries.
Significant research effort has been devoted in
classifying [supply-chain compromises](https://github.com/IQTLabs/software-supply-chain-compromises/blob/master/software_supply_chain_attacks.csv) and
developing tools for hardening the supply chain infrastructure is a trending and marketable business.
We have seen the rise of tools to mitigating the risks (e.g., [Snik](https://snyk.io/, [Sonarqube](https://www.sonarqube.org/),
and [Chaos Monkey](https://netflix.github.io/chaosmonkey/))).
Existing tools are mostly focused on monitoring applications' behavior, scanning dependencies, and assessing code quality.
However, the adoption of such tools is still at an early stage in most organizations.

![](/img/oss-supply-chain-attacks-taxonomy.png)

Typosquatting is a type of cyber attack in which an attacker creates a malicious website or software package that is designed to be similar to a legitimate
website or software package, but with a slightly different spelling or domain name.
The intention is to trick users into visiting the malicious site or downloading the malicious software by mistaking it for the legitimate site or software.

Here is an example of typosquatting in Python:

````python
# Legitimate website
legitimate_website = "www.example.com"

# Malicious website
malicious_website = "wwww.examplle.com"

# Check if the user typed in the correct website
if user_input == legitimate_website:
  # Redirect the user to the legitimate website
  redirect(legitimate_website)
else:
  # Redirect the user to the malicious website
  redirect(malicious_website)
````

In this example, the attacker has created a malicious website with a slightly different spelling than the legitimate website.
If the user types in the correct website, they will be redirected to the legitimate site.
However, if the user makes a typo and types in the malicious site, they will be redirected to the malicious site instead.
This can be used to trick the user into visiting...

## Compromising a developer's computer

One potential attack vector for OSS supply chain attacks is to compromise a developer's computer and modify the software as it is being developed.
This can be done through various means, such as phishing attacks, malware infections, or physical access to the computer.
For example, an attacker could send a phishing email to a developer that appears to be from a legitimate source and contains a link to a malicious website.
If the developer clicks the link and enters their login credentials, the attacker can gain access to the developer's computer and potentially install malware or
other malicious software.
Alternatively, the attacker could physically access the developer's computer and install malware or modify the software directly.

## Gaining access to the source code repository

Another potential attack vector is to gain access to the source code repository for an OSS project and modify the code without the knowledge of the other
developers.
This can be done through various means, such as exploiting vulnerabilities in the version control system or by compromising the credentials of a developer with
access to the repository.
For example, an attacker could find a vulnerability in the version control system that allows them to gain unauthorized access to the repository.
Alternatively, the attacker could use phishing or other means to obtain the login credentials of a developer with access to the repository and use those
credentials to make changes to the code.

## Distributing a compromised version of the software

An attacker can also distribute a compromised version of the software through unofficial channels, such as through a malicious website or via email.
This can be effective if the software is not widely distributed and users are not aware of the official distribution channels for the software.
For example, an attacker could set up a website that looks like the official website for an OSS project and offer downloads of the software from that site.
If users download the software from the malicious site, they may unknowingly install a compromised version of the software.

## Tampering with the build process

Another potential attack vector is to modify the build process for the software in order to include malicious code in the final product.
This can be done by compromising the build server or the build infrastructure. For example, an attacker could gain access to the build server and modify the
build scripts to include malicious code in the final product.
Alternatively, the attacker could compromise the infrastructure used to build the software, such as by modifying the libraries or other dependencies used in the
build process.

## Compromising the distribution channels

An attacker can also compromise the distribution channels for the software, such as the website or package repository, and replace the legitimate software with
a compromised version.
This can be effective if users are not vigilant about verifying the authenticity of the software they download.
For example, an attacker could compromise the website for an OSS project and replace the legitimate software downloads with compromised versions.
Alternatively, the attacker could compromise a package repository and replace the legitimate software packages with compromised versions.
Users who download the software from these compromised channels may unknowingly install a compromised version of the software.

# Safeguarding Against OSS Supply Chain Attacks

[//]: # (From my blog)
Overall, supply chain-related attacks are perceived as very dangerous and hard to detect.
Securing the software supply chain requires a continuous assessment of the components, vendors, and the whole operational environment.
This can only be achieved through the gathering and analysis of relevant and verifiable data sources.
[Reproducible builds](https://reproducible-builds.org/docs/) are a set of software development practices that create an independently verifiable path from
source to binary code.
A build is reproducible if given the same source code, build environment and build instructions, any party can recreate bit-by-bit identical copies of all
specified artifacts.
This build methodology allows verifying that no vulnerabilities or backdoors have been introduced in the supply chain.

Notice that to achieve reproducible builds, the CI/CD system needs to be made entirely deterministic: modifying a given source must always create the same
result.
For example, the current date and time must not be recorded and outputs always have to be written in the same order.
Furthermore, the set of tools used to perform the build and, more generally, the building environment should either be recorded or pre-defined.
Developers should have a way to recreate a close enough build environment, perform the build process, and validate that the output matches the original build.

In the supply chain, software products, including security tools, should be designed with failure in mind (i.e., they must fail gracefully).
The system should closely monitor any third-party software releases used, watch published vulnerability announcements, and distribute updates.
Notice that the [security tools themselves](https://googleprojectzero.blogspot.com/2016/06/how-to-compromise-enterprise-endpoint.html) are not exempt.

Open-source software supply chain attacks can be difficult to detect and prevent, as the open-source nature of the software makes it difficult to track the
source of the malicious code.
However, there are several measures that can be taken to safeguard against these types of attacks.
By following these best practices, open-source software projects and their users can help protect against supply chain attacks and reduce the risk of
compromise.
However, it is important to note that no security measure is foolproof, and it is always necessary to remain vigilant and stay up to date with the latest
threats and best practices in order to effectively safeguard against supply chain attacks.

## Implement secure development practices

It is important for open-source software projects to have strong security measures in place during the development process.
This can include code reviews, secure coding practices, and regular security assessments of the codebase.
By following these practices, it can be more difficult for an attacker to insert malicious code into the software without being detected.

## Use secure version control systems

The version control system used to manage the source code for an open-source software project should be secure and properly configured to prevent unauthorized
access.
This can include measures such as multi-factor authentication, access controls, and regular security audits.

## Verify the authenticity of software downloads

Users of open-source software should be vigilant and only download software from trusted sources.
It is important to verify the authenticity of software downloads, especially if they are obtained from unfamiliar websites or through email.
This can include checking the digital signature of the software and comparing it to the official signature of the software project.

## Keep software up to date

It is important to keep open-source software up to date with the latest patches and updates.
These updates may include security fixes that can help protect against supply chain attacks.
Users should enable automatic updates, if available, or regularly check for and install updates manually.

## Use secure distribution channels

Open-source software projects should use secure distribution channels to distribute their software.
This can include using official websites, package repositories, and other trusted channels to distribute software updates and new releases.

## Use security tools

There are a variety of security tools that can help protect against open-source software supply chain attacks.
These can include antivirus software, firewalls, and other security measures that can help detect and prevent malicious code from being executed on a user's
computer.

## DIY

### _Novice_ 👾

- TODO
- TODO
- TODO

### _Expert_ 💯

- TODO
- TODO
- TODO

# References

[^1]: [Backstabber’s Knife Collection: A Review of Open Source Software Supply Chain Attacks](https://arxiv.org/pdf/2005.09535.pdf)
[^2]: [SoK: Taxonomy of Attacks on Open-Source Software Supply Chains](https://arxiv.org/pdf/2204.04008.pdf)
[^3]: [Perspectives on The SolarWinds Incident](https://ieeexplore.ieee.org/document/9382367)
[^4]: [Securing the World's Software](https://arxiv.org/ftp/arxiv/papers/2110/2110.10246.pdf)
[^5]: [USA Securing Open Source Software Act of 2022](https://www.govinfo.gov/content/pkg/BILLS-117s4913is/pdf/BILLS-117s4913is.pdf)  
