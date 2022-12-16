---
layout: default
title: Vulnerabilities
parent: Security
nav_order: 2
description: "This chapter deals with the code vulnerability management"
---

# Vulnerabilities

A vulnerability is an intentional or unintentional exploitable weakness in the software. When discovered, it is usually reported back to the community and to vulnerability databases for awareness. A preferred consumption behavior is to contribute/report any detected weaknesses.

The responsibility to be aware of the security status and to update the affected software lies with the open source consumer whenever a patch or update is made available by the developing open source community.

### _Outline_ 📋
In this chapter, we learn about
- How to check the vulnerability [status](#status) of an open source component. 
- How to [identify](#identification) the vulnerabilities.
- How to [monitor](#monitoring) for vulnerabilities.
- How to quantify their [impact](#impact).
- How to [manage](#vulnerability-management) them effectively.
- [Exercises](#exercise) for the reader


## Status
If an open source component of a specific version has an vulnerability or not can be checked by looking up the component in a vulnerability database such as the NVD provided by NIST. Commercial tool providers like Synopsys, MEND, SNYK and others also provide vulnerability status are often trusted reporters to the vulnerability databases.

## Identification
When looking up the vulnerability status of your open source component in a vulnerability database it’s vital to check for the correct component. Technics for assisting such identification do exist, but unfortunately, there is no uniform or standardized way of providing identification of an open source component.
Efforts like the Common Platform Enumeration (CPE) by National Institute of Standards and Technology (NIST) or the Universally Unique Identifier (UUID) by
Open Software Foundation (OSF) both has their pros and cons, and none is without the risk of misidentification even if both are used.

## Monitoring
Vulnerability monitoring shall be performed both while development is ongoing but also after development has been concluded to swiftly be able to take mitigation action.
Monitoring of vulnerability status can be performed manually or automatically with the help of commercial or open source tools with awareness of included open source and connection to vulnerability database(s).

## Impact
Analysis of possible impact and vulnerability exposure shall be performed upon discovery of a reported and included open source component in your use. Depending on the result of such analysis it should be possible to understand if the vulnerability can be exploited in your implementation or not. If true, the recommended solution should be implemented, if any such exist, and replace any exposed installations.

## Vulnerability management
The Common Vulnerability Scoring System (CVSS) is a method used to supply a qualitative measure of severity. CVSS is not a measure of risk. CVSS consists of three metric groups: Base, Temporal, and Environmental. The Base metrics produce a score ranging from 0 to 10, which can then be modified by scoring the Temporal and Environmental metrics.
Depending on the vulnerability severity/CVSS scoring/support context/community status and the impact on your product/solution you might need to consider alternative remediation paths, such as:
- Temporary own fix with/without feedback to the community
- Wait for next version by the community
- Back porting of solution to your older version
- Relying on your supplier for patch/correction
Part of the vulnerability management should be to update the company database of the detected status to avoid future selection/use of the component.

## DIY
  - Who is responsible for updating a software to avoid vulnerabilies?
      - The Developer who wrote the original software 
      - The consumer of the open source software (correct)
      - The end user of the application 
      - The corporate security officer 
  - When should vulnerability monitoring be performed?
      - Before an open source software is introduced
      - While development is ongoing (correct) 
      - When software is in production (correct)
      - All of the above
