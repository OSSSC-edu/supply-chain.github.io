---
layout: default
title: Vulnerabilities
parent: Security
nav_order: 2
description: "This chapter deals with the code vulnerability management"
---

# Vulnerabilities

A vulnerability is an intentional or unintentional, exploitable weakness in the software. When discovered, it is usually reported back to the community for fixes, and to vulnerability databases for awareness. A preferred consumption behavior is to contribute/report any detected weaknesses. The responsibility to be aware of the security status of a software program, and to update the affected software, lies with the open-source consumer, whenever a patch or update is made available by the developing open-source community.

### _Outline_ 📋
In this chapter, we learn about
- Checking the vulnerability [status](#status) of an open source component
- [Identifying](#identification) the vulnerabilities
- [Monitoring](#monitoring) for vulnerabilities
- Quantifying the [impact](#impact) of vulnerabilities
- [Managing](#management) vulnerabilities effectively

We also encourage you to explore the links throughout the text, and the [Do-It-Yourself](#diy) tasks.

## Status

Checking for vulnerabilities in an open-source software program, or dependency, can be done by scanning well-known vulnerability databases, such as Common Vulnerabilities and Exposures, or [CVE](https://en.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures), or the National Vulnerability Database, or [NVD](https://nvd.nist.gov/), provided by the National Institute of Standards and Technology ([NIST](https://www.nist.gov/)). Commercial tool providers like [synopsys](https://www.synopsys.com/), [MEND](https://www.mend.io/), [synk](https://snyk.io/), and others also provide vulnerability status, and are often trusted reporters to the vulnerability databases.

## Identification

When looking up the vulnerability status of an open-source software package in a vulnerability database, it is vital to check for the correct component. Techniques for assisting this identification do exist, but unfortunately, there is no uniform or standardized way of doing so. Efforts like the Common Platform Enumeration ([CPE](https://nvd.nist.gov/products/cpe)) by NIST, or the Universally Unique Identifier (UUID) by Open Software Foundation (OSF) both have their pros and cons, and none is without the risk of misidentification, even if used together.

## Monitoring

Vulnerability monitoring should ideally be performed both during development, as well as after development. This is done so as to swiftly be able to take mitigative actions. Regular monitoring of the vulnerability status of all components in the supply chain may be performed manually or automatically, with the help of commercial or open-source tools, that are synchronized with vulnerability database(s).

## Impact

The analysis of the possible impact of vulnerability exposures should be performed upon discovery of a reported and included in the supply chain of a software project. Depending on the result of this analysis, it should be possible to understand if and how the vulnerability may be exploited by malicious actors. The vulnerability should be promptly managed, in the exposed installations.

## Management

The Common Vulnerability Scoring System, or [CVSS](https://www.first.org/cvss/), is a method used to supply a qualitative measure of the severity of a vulnerability. CVSS is not a measure of risk. CVSS consists of three metric groups: Base, Temporal, and Environmental. The Base metrics produce a score ranging from 0 to 10, which can then be modified by scoring the Temporal and Environmental metrics. Depending on the vulnerability severity, CVSS scoring, support context, community status, and the impact on the software project, developers can consider remediation paths, such as:
- Temporary own fix with or without feedback to the community
- Wait for the next version by the community
- Back-porting of project to an older version
- Relying on the supplier for a patch or correction
An important aspect of vulnerability management should also be to update the database of the organization to include the detected status, to avoid future selection and use of the component.

## DIY

- Who is responsible for updating a software to avoid vulnerabilies
  - The Developer who wrote the original software
  - The consumer of the open source software
  - The end user of the application
  - The corporate security officer
- When should vulnerability monitoring be performed
  - Before an open-source software is introduced
  - While development is ongoing
  - When software is in production
  - All of the above
