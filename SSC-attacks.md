---
layout: default
title: OSS Supply Chain Attacks
parent: OSS Supply Chain
nav_order: 1
---

# OSS Supply Chain Attacks

Open-source software (OSS) [supply chain attacks](https://en.wikipedia.org/wiki/Supply_chain_attack) are a type
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

### _Outline_ 📋

In this chapter, we learn about:

- A real-world example of a [software supply chain attack](#example--the-solarwinds-supply-chain-attack)
- A taxonomy of the principal [attack vectors in OSS supply chain attacks](#attack-vectors-in-oss-supply-chain-attacks)
- Techniques, methodologies, and tools to [detect and prevent OSS supply chain attacks](#safeguarding-against-oss-supply-chain-attacks)

We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in
the [references](#references).

## Example: The SolarWinds Supply Chain Attack

The SolarWinds attack was a major software supply chain attack that occurred in 2020.
It is a typical example of the fragility that permeates modern software supply chains.
The attack involved the compromise of the software supply chain of [SolarWinds](https://www.solarwinds.com/), an American company that provides IT management
software to government agencies and businesses around the world.

In this case, a malicious actor gained access to the Orion monitoring and management system operated by SolarWinds and inserted malicious code into the
deployment infrastructure.
Interestingly, changes were done at the source code level, which means that code was tested, signed, and released through the SolarWinds' CI/CD platform, and
nobody in
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

> At the moment, governments have been somewhat ineffectual in handling supply-chain issues.[^3]

Incidents at this scale are evidence of the lack of awareness related to software supply chains, and the lack of control of companies and the government
regarding the software products and services deployed to their clients.[^4]
But on the other hand, mass-scale software development and future global innovation are at risk if governments enforce more restrictive security gates to
prevent incidents such as the SolarWinds.
Technology-based solutions need to be developed in order to cope with the challenges of identifying the attack vectors and providing safeguarding mechanisms for
[securing the software supply chain](https://www.cesarsotovalero.net/blog/the-software-supply-chain.html).

## Attack Vectors in OSS Supply Chain Attacks

Using third-party OSS dependencies to help build and develop large software solutions is now a necessity for most companies.
However, relying on external components that are not developed in-house comes at a cost, as vulnerabilities discovered in OSS libraries may affect the dependent
applications.
OSS components with known vulnerabilities is included in the [OWASP Top 10 Application Security Risks](https://owasp.org/www-project-top-ten/) since 2013.
If a single part of the supply chain is compromised, the entire system could be vulnerable to an attack.

Supply chain attacks are difficult detect because software continuously change products throughout the development process.
From source code to a running application in the cloud, attackers may target any part of the supply chain, including tools used in the development process, but
often focus on the weaker links and take advantage of the trust that allows for code reuse. It is
expected that attacks on third-party components will increase in the coming years.
Therefore, attacks targeting third-party dependencies are expected to become more prominent over the next few years.

> “Projects often incorporate code and libraries from many sources with unknown provenance...” ― <cite><a href="http://web.mit.edu/ha22286/www/">Hamed
> Okhravi</a></cite>

Package managers are particularly susceptible to many kinds of supply chain attacks (
e.g., [typosquatting](https://news.ycombinator.com/item?id=11862217), [cryptojacking](https://www.kaspersky.com/resource-center/definitions/what-is-cryptojacking),
and [malicious contributors](https://www.cybersecuritydive.com/news/github-commits-malicious-code/627466/)).[^1]
This is due to the lack of efficient mechanisms for detecting malicious code injected into packages uploaded to popular package repositories.
For example, there were no security audit performed on the packages submitted to the largest repository of JavaScript libraries `npm` prior to `npm@6`.
Significant research effort has been devoted in
classifying [supply-chain compromises](https://github.com/IQTLabs/software-supply-chain-compromises/blob/master/software_supply_chain_attacks.csv) and
developing tools for hardening the supply chain infrastructure is a trending and marketable business.
We have seen the rise of tools to mitigating the risks (e.g., [Snik](https://snyk.io/, [Sonarqube](https://www.sonarqube.org/),
and [Chaos Monkey](https://netflix.github.io/chaosmonkey/))).
Existing tools are mostly focused on monitoring applications' behavior, scanning dependencies, and assessing code quality.
However, the adoption of such tools is still at an early stage in most organizations.

Ladisa et. al.[^2] created a taxonomy of OSS supply chain attacks with the help of 17 domain experts.
They identify 107 unique attack vectors taking the form of an attack tree in which the attacker’s top-level goal is to inject malicious code into
open-source project artifacts, which are consumed and executed by downstream users.

The following figure, from the original paper, shows a excerpt of the attack tree.

![](/img/oss-supply-chain-attacks-taxonomy.png)

The previous figure reflects the feedback of 17 domain experts on the initial version, collected through an online survey.
As observed, subtrees for user and system compromises exist multiple times, only their first occurrence is expanded. The grey, numbered rectangles
illustrate the different criteria used for structuring the tree. Each node has references to both Scientific Literature (SL) and
Gray Literature (GL).
For the complete taxonomy, see the [online explorer for software supply chains](https://sap.github.io/risk-explorer-for-software-supply-chains/) website.

In the following sections, we cover the most common attack vectors of OSS supply chain attacks in more details.

### _Compromising the developer's computer_

One potential attack vector for OSS supply chain attacks is to compromise a developer's computer and modify the software as it is being developed.
This can be done through various means, such
as [phishing attacks](https://en.wikipedia.org/wiki/Phishing), [malware infections](https://en.wikipedia.org/wiki/Malware),
or [physical access to the computer](https://en.wikipedia.org/wiki/Physical_access).
For example, an attacker could send a phishing email to a developer that appears to be from a legitimate source but that contains a link to a malicious website.
If the developer clicks the link and enters their login credentials, the attacker can gain access to the developer's computer and potentially install malware or
other malicious software.
Alternatively, the attacker could physically access the developer's computer and install malware or modify the software directly.

### _Modifying the source code repository_

Another potential attack vector is to gain access to the source code repository for an OSS project and modifying the code without the knowledge of the other
developers.
This can be done through various means, such as exploiting vulnerabilities in the version control system or by compromising the credentials of a developer with
access to the repository.
For example, an attacker could find a vulnerability in the version control system that allows them to gain unauthorized access to the repository.
Alternatively, the attacker could use phishing or other means to obtain the login credentials of a developer with access to the repository and use those
credentials to make changes to the code.

A typical example is of becoming a contributor of a popular OSS project.[^6]
In this case, an attacker convinces or tricks a legitimate project maintainer (e.g., by using social engineering techniques) to provide him or her additional
permissions. This way, the project maintainer could promote the attacker as a role of maintainer or even project owner. As a result, the attacker receives
privileges for project-related resources, e.g., the source code repository, the build system or the database administration.
Unfortunately, many open-source projects are anyways short on resources (cf. https://www.codeshelter.co/ or https://jazzband.co), and sometimes the original
maintainers simply
cannot or do not want to continue project maintenance anymore, both of which makes such
projects prone for these social-engineering attacks.

### _Distributing a compromised version of the software_

An attacker can also distribute a compromised version of the software through unofficial channels, such as through a malicious website or via email.
This can be effective if the software is not widely distributed and users are not aware of the official distribution channels for the software.
For example, an attacker could set up a website that looks like the official website for an OSS project and offer downloads of the software from that site.
If users download the software from the malicious site, they may unknowingly install a compromised version.

A typical example is to develop and advertise distinct malicious package from scratch.[^8]
This attack vector covers the creation of a new, seemingly legitimate and useful open-source project with the intention to use it for spreading malicious code,
either from the beginning or at a later point in time. Besides creating the project and developing useful functionality, the attacker is required to advertise
the project in order to attract victims.

Another way is polluting [package managers](package-managers.md#package-managers) by creating name confusion with legitimate packages (e.g., typosquatting,
combosquatting, or brandjacking).[^9]
The general idea behind name confusion is that attackers craft new component names that resemble names of legitimate open-source or system components, suggest
trustworthy authors or play with common naming patterns in different languages or ecosystems. Malicious components with such names are then deployed on source
code or package repositories waiting to be downloaded by victim users or developers. Since the package name does not yet exist in the respective repository, the
deployment can be done very easily, without interfering with any legitimate packages, including the one(s) that inspired the new name. Child nodes of this
attack vector relate to sub-techniques applying different modifications to the legitimate project name.

We are going to discuss now typosquatting, which is a type of cyber attack in which an attacker creates a malicious website or software package that is designed
to be similar to a legitimate website or software package, but with a slightly different spelling or domain name.
The intention is to trick users into visiting the malicious site or downloading the malicious software by mistaking it for the legitimate site or software.

Here is an illustrative code example of typosquatting in Python:

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

### _Tampering with the build process_

Another potential attack vector is to modify the build process for the software in order to include malicious code in the final product.
Build jobs consume project sources to produce binary artifacts that can be readily used or deployed. Ideally, build jobs are defined in the source code
repository itself, but they can also be read from other sources or be manually created using Web interfaces of build systems like Jenkins. In the latter cases,
attackers can impersonate the maintainer in order to change the build job definition such that malicious code is injected into the final software product.
Tampering the build process can be done by compromising the build server or the build infrastructure. For example, an attacker could gain access to the CI
server and modify the build scripts to include malicious code in the final product.
Alternatively, the attacker could compromise the infrastructure used to build the software, such as by modifying the libraries or other dependencies used in the
build process.

Many systems used throughout software development are OSS themselves, e.g., plugins for Jenkins, Maven or Visual Studio Code, or integrate OSS
components. A typical example of infecting the build process by inserting malicious components,[^7] just as with the SolarWinds example discussed previously.
A compromised build tool, for instance, can infect any software built using that tool, along the lines of the famous "Reflections on Trusting Trust" paper
from K. Thompson.[^13] The infection of components through the infection of open-source used during development, build and distribution thereby corresponds to
the recursive application of the attack tree.

Another case is tampering version control systems.[^10]
Open-source based software development relies on multiple systems, many of which are accessible online, e.g., source code repositories or build systems. Those
systems can be subject to vulnerabilities, require secure configuration settings and come with privileged administrator accounts. In this specific case, the
modification of a legitimate package, plugin or configuration file to include something malicious could be achieved by attacking the version control system on
which such files are stored. Though the majority of open-source projects is hosted on GitHub or GitLab cloud services, some projects and open-source foundations
still operate their own versioning control system.

### _Compromising the distribution channels_

An attacker can also compromise the distribution channels for the software, such as the website or package repository, and replace the legitimate software with
a compromised version.
This can be effective if users are not vigilant about verifying the authenticity of the software they download
(a.k.a [software integrity](oss-supply-chain-integrity.md)).
For example, an attacker could compromise the website for an OSS project and replace the legitimate software downloads with compromised versions.
Alternatively, the attacker could compromise a package repository and replace the legitimate software packages with compromised versions.
Users who download the software from these compromised channels may unknowingly install a compromised version of the software.

## Safeguarding Against OSS Supply Chain Attacks

Overall, supply chain-related attacks are perceived as very dangerous and hard to detect.
Securing the software supply chain requires a continuous assessment of the components, vendors, and the whole operational environment.
This can only be achieved through the gathering and analysis of relevant and verifiable data sources.
In the supply chain, software products, including security tools, should be designed with failure in mind (i.e., they
must [fail gracefully](https://en.wikipedia.org/wiki/Graceful_exit)).
The system should closely monitor any third-party software releases used, watch published vulnerability announcements, and distribute updates.
Notice that the [security tools themselves](https://googleprojectzero.blogspot.com/2016/06/how-to-compromise-enterprise-endpoint.html) are not exempt.

There are several measures that can be taken to safeguard against OSS supply chain attacks.
By following good practices, OSS projects and their users can help protect against supply chain attacks and reduce the risk of compromise.
However, it is important to note that no security measure is foolproof, and it is always necessary to remain vigilant and stay up to date with the latest
threats and best practices in order to effectively safeguard against supply chain attacks.

The following sections give detail on some of the best practices that can be used to safeguard against the most common supply chain attacks.

### _Implementing secure development practices_

It is important for OSS projects to have strong security measures in place during the development process.
This can include code reviews, secure coding practices, and regular security assessments of the codebase.
By following these practices, it can be more difficult for an attacker to insert malicious code into the software without being detected.

The build service and build jobs should ensure that individual builds run in an isolated environment (e.g., in Docker containers), such that one build can
neither influence the build service as a whole nor other builds of the same or other development projects. In particular, this concerns access to shared
resources like download caches.
On the other hand, making a [build reproducible](SSC-reproducible-builds.md) allows to verify that no vulnerabilities or malicious code has been introduced
during the build process. Identical results for every build of a given source allow multiple parties to come to a consensus and to highlight any deviations from
the expected
build result. Reproducible builds firstly require a deterministic build system. Secondly, the build environment should either be recorded or pre-defined.
Finally, users will be given a way to
recreate such build environment, perform the build process and so validate that the output matches the intended one.

[The Software Bill of Materials (SBOM](https://ntia.gov/page/software-bill-materials)) is a list of components related to a given software artifact, comparable
to the list of ingredients on food packaging.[^12]
Those components are typically runtime dependencies of the artifact in question, but can also comprise other dependency types. The content and properties of
SBOMs decide about use-cases and capabilities, esp. the kind of verifications that can be exercised by downstream consumers. For instance, SBOMs can be
machine-readable, timestamped and signed, whereas individual dependencies can be identified using consistent naming schemes and digests, and described in regard
to provenance and pedigree. The creation of SBOMs can be automated. As per today, [SPDX](https://spdx.dev/), [OWASP CycloneDX](https://cyclonedx.org/),
and [SWID](https://nvd.nist.gov/products/swid) are prominent machine-readable standards and formats for SBOMs.

### _Using secure version control systems_

Version control systems are used to manage the source code for an OSS project.
They should be secure and properly configured to prevent unauthorized access.
This can include measures such as [multi-factor authentication](https://en.wikipedia.org/wiki/Multi-factor_authentication), access controls, and regular
security audits.

For example, implementing manual source code reviews can help prevent malicious code from being introduced into the software.
Manual source code reviews comprise the inspection of a software's entire code base by a human reviewer in order to identify security flaws or malicous code.
They can outperform automated tools in the detection of certain vulnerability types, e.g. flaws in application/business logic or authorization checks. However,
manual source code reviews are slow and require skilled, experienced and patient code reviewers. As such, they are more suitable for highly sensitive projects,
e.g. in military contexts or critical infrastructures, especially when considering that such reviews have to be performed for all direct and transitive
dependencies of a given development project.

### _Verifying the authenticity of software downloads_

Users of open-source software should be vigilant and only download software from trusted sources (i.e., through the official releasing channels).
It is important to verify the authenticity of software downloads, especially if they are obtained from unfamiliar websites or through email.
This can include checking the digital signature of the software and comparing it to the official signature of the software project.

For example, integrity check of dependencies through cryptographic hashes can be used to verify the authenticity of software downloads.
Developers can verify the integrity of their direct and transitive dependencies by specifying and checking cryptographic hashes, e.g. `SHA-256` or `SHA-512`
digests. This supports detecting a later compromise of those packages in, e.g., local build system caches, internal repository mirrors or even public package
repositories.

The following is an example of using the `openssl` utility to verify the integrity of a package using the `SHA-256` hash on Linux:
Replace `<public-key-file>`, `<signature-file>`, and `<software-package>` with the appropriate filenames.

```bash
openssl dgst -sha256 -verify <public-key-file> -signature <signature-file> <software-package>
```

Another example is by using preventive squatting.
Package names that resemble legitimate ones can be proactively registered by benign parties before they can be squatted by attackers. This technique can be
applied by package repositories (e.g. npm package `epress`), project maintainers (e.g., PyPI package `bs4`) or other parties. However, since the number of
candidate package names can be very large, it seems impossible to preventively register all of them.

### _Keeping software up to date_

It is important to keep OSS up to date with the latest patches and updates.
These updates may include security fixes that can help protect against supply chain attacks.
Users should enable automatic updates, if available, or regularly check for and install updates manually.
There are many tools available that can help to automatically update software projects. For example, [Renovate](https://github.com/renovatebot/renovate)
and [Dependabot](https://github.com/dependabot) are popular GitHub bots used to
automatically update dependencies in a variety of programming languages, including JavaScript, Python, and Java. is another GitHub bot.
They then create pull requests with updated dependencies, which can be reviewed and merged by the
project maintainers. Other tools that can help to automatically update software projects
include [Greenkeeper](https://greenkeeper.io/), [Snyk](https://snyk.io/), and [NPM-check-updates](https://www.npmjs.com/package/npm-check-updates). These tools
are important because they help to ensure that software projects are kept up to date with the latest security patches and performance improvements, which can
help
to improve the security, performance, and reliability..

### Removing unused dependencies

Software developers declare direct dependencies on open-source components whose functionality they want to use in the software under development or during
development, e.g. compile dependencies or build plugins.[^11]
Those dependencies have their own dependencies, so-called indirect or "transitive dependencies", all of
which are automatically resolved and downloaded by package managers like Gradle or npm. However, some of those transitive dependencies may not be needed in the
specific development context, e.g. because a certain functionality of a direct dependency is not used. While the removal of such "bloated dependencies" can
reduce the supply chain's attack surface, their identification is not straight-forward, e.g. due to dynamic programming features.

There are several tools that can help to identify and remove unused dependencies.
For example, [DepClean](https://github.com/castor-software/depclean) automatically removes unused dependencies in Java Maven projects.
It removes all the dependencies that are included in the project's dependency tree but are not actually necessary to build it. DepClean detects and removes all
the unused dependencies declared in the `pom.xml` file of a project or imported from its parent. It can be executed as a Maven goal through the command line or
integrated directly into the Maven build lifecycle (CI/CD).

### _Relying on secure distribution channels_

OSS projects should use secure distribution channels to distribute their software.
This can include using official websites, package repositories, and other trusted channels to distribute software updates and new releases.
Sandboxes offer isolated and instrumented environments, that are typically used to separate and prevent harmful execution from tampering with other resources in
a system. By executing open-source components in isolated environments during their consumption would prevent infections or unauthorized access to system or to
sensitive resources.

[Code signing](https://en.wikipedia.org/wiki/Code_signing) is a process by which a software publisher signs their software with a digital signature, which can
be verified by the end user.
Code signing enforces binary and application integrity, hence ensures that a program comes from a valid source (authenticity) and that has not been modified
since it was signed (integrity). The efficacy of the code signing depends on the security of the underlying cryptographic mechanism and the related signing
keys. Note that the validation of digital signatures and digests cannot protect against attacks that target the build process to inject malicious code. In fact,
the signing process typically happens at the end of the build process at a time when potentially malicious tests and build plugins were already executed.It must
be noted that the efficacy of code signing as a preventive safeguards depends on the scrutiny of the consumer when verifying the signature.

### _Using security tools_

There are a variety of security tools that can help protect against OSS supply chain attacks.
These can include antivirus software, firewalls, and other security measures that can help detect and prevent malicious code from being executed on a user's
computer.

On the other hand, security, quality and health metrics help to assess the security posture of an open-source project and the security risks resulting from its
use. Such metrics may consider, for instance, information about the liveliness of a project or whether given security best-practices are applied. They help end-users to decide
which components to consume by making them aware of the security implications, and can be computed prior to the first use but also on a continuous basis for
dependencies established in the past.

## DIY

### _Novice_ 👾

- Get familiar with the [OWASP Top 10 Application Security Risks](https://owasp.org/www-project-top-ten/).
- Explore the attack tree, attack vectors, and safeguards in
  the [Risk Explorer for Software Supply Chains](https://sap.github.io/risk-explorer-for-software-supply-chains/#/).

### _Expert_ 💯

- Scan the consumed open-source components of a software project and assess the security requirements at each step of the supply chain.
- Design the collaboration to an OSS such that they accept contributions only via pull/merge requests while enforcing a review process and a discussion before
  merging the code in production branches.
- Execute a vulnerability assessment tool to find for vulnerabilities in a software project.

## References

[^1]: [Backstabber’s Knife Collection: A Review of Open Source Software Supply Chain Attacks](https://arxiv.org/pdf/2005.09535.pdf)
[^2]: [SoK: Taxonomy of Attacks on Open-Source Software Supply Chains](https://arxiv.org/pdf/2204.04008.pdf)
[^3]: [Perspectives on The SolarWinds Incident](https://ieeexplore.ieee.org/document/9382367)
[^4]: [Securing the World's Software](https://arxiv.org/ftp/arxiv/papers/2110/2110.10246.pdf)
[^5]: [USA Securing Open Source Software Act of 2022](https://www.govinfo.gov/content/pkg/BILLS-117s4913is/pdf/BILLS-117s4913is.pdf)
[^6]: [Small World with High Risks: A Study of Security Threats in the npm Ecosystem](https://www.usenix.org/conference/usenixsecurity19/presentation/zimmerman)
[^7]: [SolarWinds and the Challenges of Patching: Can We Ever Stop Dancing With the Devil?](https://escholarship.org/content/qt0m27w0hf/qt0m27w0hf.pdf)
[^8]: [Practical Automated Detection of Malicious npm Packages](https://arxiv.org/pdf/2202.13953.pdf)
[^9]: [SpellBound: Defending Against Package Typosquatting](https://arxiv.org/pdf/2003.03471.pdf)
[^10]: [Security in the Software Development Lifecycle](https://www.usenix.org/conference/soups2018/presentation/assal)
[^11]: [A comprehensive study of bloated dependencies in the Maven ecosystem](https://link.springer.com/content/pdf/10.1007/s10664-020-09914-8.pdf)
[^12]: [Assuring software and hardware security and integrity throughout the supply chain](https://ieeexplore.ieee.org/abstract/document/6107848)
[^13]: [Reflections on Trusting Trust](https://dl.acm.org/doi/10.1145/358198.358210)