---
layout: default
title: Fundamentals
nav_order: 2
has_children: true
permalink: /fundamentals2
---

# Community development

## Forming a community of contributors
The nature of the open source licensing combined with the availability of the source code for all to explore, modify and use is what enable engagement and contribution from other developers. This is the reason why free open source software projects have multiple contributors, who contribute in various ways, such as by implementing new features, testing, fixing bugs, translation, and documentation.
The free open source movement stems from engagement and contributions from individuals and organisations with different backgrounds, motivations, reasons, expertise, and geographical locations.
The size of community for an open source project may vary over time and has typically a core of developers who together drives the project in a certain direction. Sometimes communities split over different opinions of development direction and a spin-off, or fork, appears as a new community serving the alternative development direction.
Measuring the community engagement and understanding the future development direction is important for successful professional consumption and contribution of a free open source software.

## Software repository, a community collaboration enabler
Distributed open source software development by multiple contributors benefits from a shared software repository which allows developers to incrementally submit and track enhancements/modifications to the software allowing for controlled versioning and releases of selected commits with documented changes for each release.
GitHub along with GitLab, Bitbucket, Gitea and Google Developers are platforms providing such repository service to open source projects. Platforms like these also provide metrics such as number of commits, stars and forks which can help in determining the activity and popularity of a project as illustrated by the examples of Te2zos and MongoDB:

 
# Consumption and Compliance 

Free open source software has become a fundamental building block of commercial software across most industry categories. The business reasons for consuming free open source software range from leveraging common functionality for lowering development costs, via alignment with open APIs, to participation in entire ecosystems based on customer demand.
In any case, consuming free open source software must always be based on a clear understanding of the business rationale as well as mid- and long-term implications and not only the obvious short-term gain. In particular, any professional consumption of free open source software needs to make sure to be in compliance with not only the granted license terms but also the company policy for developing with free open source software.
Additionally, consuming free open source software comes with security considerations needed and possible activities to identify and mitigate potential risks. Examples of these are, awareness of community producing and maintaining as well as the software itself and what it might contain.
Consumption can be subdivided in mainly two areas such as 1) product development and 2) supporting systems for product development. Different policies can be applied for managing risk exposure and dependencies.

##Strategy/policy
The company needs to have a strategy and/or policy in place on how to develop with open source software included in its products. This involves having a structure in place where decisions for what and how such development can take place, but also what free open source software to allow or not and in what type of development.
Such strategy or policy might also be needed on product or product area level.

 
The strategy for consuming free open source software should consider the following aspects:
-	Community and project health: This includes, but isn’t limited to, aspects such as activity of the community, number of contributors and diversity of contributing organizations. The purpose of these aspects is to allow a risk analysis regarding future stability and dependability of the open source component. These aspects should be recurringly reviewed. 

In all cases of consumption of free open source software, the source code shall always be available to be able to take over the "ownership" in the case it becomes necessary. For instance, when the community changes the license to become unusable for the intended purpose, or the community just fades or gets lost.

-	Security: Free open source software is effectively being developed, hosted, and built by external developers and on external infrastructure. As a result, it is imperative to conduct security scans of all open source software before consumption, targeting malware as well as known vulnerabilities. Additionally, a risk assessment of using a given free open source software as part of a commercial product should be conducted. Finally, once introduced into product development, every free open source software component must be continuously monitored for vulnerabilities. 

-	License and compliancewith IPR (Inteelectual Property Rights): All usage of free open source software, internally and in products shipped to customers, must be compliant to all obligations declared in the respective open source licenses. 

## Instructions and guidance
Creation of open source instruction(s) and guidance documentation will help a company to successfully consume free open source software in a uniform, compliant and secure way.
In the absence of such instructions or guidance you need to seek or create appropriate instructions to secure the usage of open source in your project.
The instruction(s) might define roles needed to perform the open source handling within the company.
Supporting guidance documentation might help to clarify what is to be expected in the actual implementation of the instruction for open source software handling.

## Open Source Governance setup
One way of organizing the consumption within a company/corporation is by establishing a unit/team/program (usually called Open Source Program Office (OSPO)) within the company to be responsible for the company governance of free open source software.
Companies with an established OSPO tend to get more value out of its open source consumption according to recent studies performed by the Linux Foundation Research.
Other known ways to organize the consumption is by having a centralized policy group defining basic consumption rules where each development line/project can act. The drawback of this setup is the lack of opportunity to share experiences through-out the company unless there are methodology and tools supporting sharing.
There also seems to be a correlation between the size of the company and the willingness to invest in a dedicated team for open source governance where larger companies (with more employees) more often choose such a setup.
It is however noteworthy that OSPO is an implementation choice where the goals can be reached by other means.  Those goals are typically to 1. Gain a strategic view of, and engagement in open source. 2 Better leverage the free open source software consumed by the organization, 3 Manage legal risks and compliance matters in a uniform manner across the organization. 

# Available standards for open source compliance

## Open source handling process
The purpose of a common free open source software handling process is to achieve a uniform way of working within the whole company. Such a process supports the possibility to provide an auditable description of the open source handling and thus providing trust, and possibly fulfilling regulatory requirements.
A company level process will most likely need to have its local adaptations to suit local development practices and/or requirements, but these should still fulfill the major intentions and checks of the overall process.
Part of such a company process is the open source introduction process which aims at having a uniform introduction with harmonized data creating company common understanding of the free open source software for development decisions.

## Roles and responsibility
When developing with free open source software several roles are needed. Most of these roles will be shared with roles for developing proprietary software but some are unique.
Open source roles need to be described in terms of obligations and mandates.
Obvious roles are the software designer and the responsible designer, but you also need roles to secure the compliance and governance part of open source development. Depending on the company structure this might be layered.

## OpenChain (ISO 5230:2020)
ISO/IEC 5230 (known as OpenChain) is an international standard on the key requirements for a high-quality free open source license compliance program. The standard was published jointly by the International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC) in late 2020. The standard is based on the Linux Foundation OpenChain Specification 2.1. It focuses on software supply chains, easier procurement and license compliance.

## Documentation of software composition
Documentation to declare included free open source software components as either a part of a license obligation, customer requirement or regulatory requirement can be done in many ways where the Software Bill of Material, SBOM, is one way of representing the product content. Either to support human or machine readability.
Suggested formats are being developed both for general consumption and for industry niches like automotive, health and telecom. There is a standard for the data format (SPDX) for this in place. ISO/IEC 5962:2021
NTIA requirements on SBOMs: https://www.ntia.doc.gov/report/2021/minimum-elements-software-bill-materials-sbom

## Security strategy when selecting open source components
The expectation that a lively and active community will provide patches/security fixes quicker is one of the drivers when selecting components.
Should you go for the latest or second latest as your strategy. Different opinions exist with pros/cons. Version upgrade compatibility is something to consider.

## Commercial vendors / Mergers & Acquisitions
Free open source software issues must also be adequately addressed in third party contracts, development agreements, distribution agreements, acquisitions, and other transactions. 

End of chapter
