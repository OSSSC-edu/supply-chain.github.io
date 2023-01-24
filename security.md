---
layout: default
title: Security
nav_order: 6
description: ""
has_children: true
permalink: /security
---

# Security overview

In the previous chapters ([Fundamentals](fundamentals.md), [OSS Supply Chain](oss-supply-chain.md)) we saw the fundamentals of Open-source software, its use in the software supply chain and cyberattacks of the past. But what differentiates open-source code, and products, from closed-source. In the latter, we know the origin of the software; we *may* trust the company that produced it; we *assume* that the software does not contain vulnerabilities. In an open-source software, the contributor of a piece of code and the provider of a library may be unknown to us; moreover, the security of the underlying code is not guaranteed. This creates the following issues:
- How can we know who produced some piece of code? Can we trust this person?
- Can we trust that this person is *actually* responsible for producing the code?
- Can we verify that the issued code has not changed?
- Is the software free from vulnerabilities? How can we attest to that?

In the overall Security chapter ([Public Key Infrastructure](SEC-pki.md), [Web of Trust](SEC-web-trust.md), [Access Control](SEC-access.md), [Vulnerabilities](SEC-vulnerabilities.md)), we will discuss the concepts of trust, its delegation, and the different systems currently in use that can provide this. How we can tie a software update to a specific individual or confer trust to some piece of data. We will list some of the best practices in the area of key management, how we can ensure access control for our repositories and various option on restricting code updates. Finally, we will address the issues of identifying vulnerabilities in part of our infrastructure, with the help of tools and the security community.