---
layout: default
title: Introduction to Open Source Security
nav_order: 2
has_children: true
permalink: /SEC-Introduction-Ind
---

# Introduction to Open Source Security
Cyber security refers to the system's ability to protect against unauthorized access or attacks. Failing to address cyber security can have severe and wide-ranging consequences, including financial losses, damage to reputation, and disruption to business operations.

It is important that everyone doing software development must take cyber security seriously and implement appropriate measures to protect against cyber threats.

Open source security refers to the measures that must be taken to ensure the security of the used free open source software. The security must be considered and addressed throughout the whole product's lifecycle.

Open source security throughout the whole product lifecycle can be seen from several aspects:
1.	The security in the FOSS itself, meaning the security features built in plus the security assurance performed.
2.	Secure consumption of it, e.g. making sure the supply chain is secure, the needed support level is sufficient for the intended use and that the FOSS is implemented and used in a correct way.
3.	Managing vulnerabilities, meaning the capability to detect vulnerabilities and update the code, test, and deliver the correction.


These aspects should be addressed through established processes and possibly tool support.
From a security concern, the benefit in using open source software is transparency since there is a “community of eyes” working with and reviewing the open source code coming from the community. It can be argued that the transparency is only true if the actual reviewing is performed by the community, and not only assumed.

Proprietary developed software provides less exposure to external bad actors but with less opportunity for reviewing and correction.
In general, open source projects with a large community can have a higher security level, but the majority of open source projects are maintained by small teams of volunteer developers and there is no guarantee that the particular team have time and resources to update their code. Those who create and contribute to open source software are not obligated to maintain it, hence it’s clearly up to the users/consumers to evaluate the security risks related to consuming the code. 

One important difference between proprietary developed code vs open source software is mainly when it comes to reporting (zero days) and the time window for fixing flaws. In general, vulnerabilities in open source software receives more public attention with the expectation for those to be corrected in a faster pace than proprietary software.

Despite the advantages of using open source it will always come with security risks. Hence, it’s important to define, as part of your open source security strategy, who is responsible for the security of the open source including dependencies and define processes and infrastructure to deal with the risks. 
It’s preferred to use tools that automatically identifies and monitors your open source software for known vulnerabilities, thereby trigger alerts providing remediation guidance. It’s important to understand the limitation of the selected tools and have an approach to handle the limitation gap.

## Software Composition Analysis (SCA)
In order to understand your security exposure, you have to know what open source components you have included in your development/product.
Awareness of such content should be created during development, assuming there is an open source handling process in place for the developers. This also includes transparency of open source content when re-using internally developed components/products.

Still, even with the best intentions and processes, there is a risk for open source content to be included by mistake. This includes significant code snippets to full components, why software composition analysis of the developed code base needs to be performed.
    
It’s preferred to use tools that automatically provides the software composition analysis for you, but it is also important to understand the limitation for the selected tool with a plan to handle the limitation gap.
