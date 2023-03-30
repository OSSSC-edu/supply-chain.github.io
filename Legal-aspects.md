---
layout: default
title: Legal Aspects
nav_order: 5
has_children: true
permalink: /legal-aspects
---

# Open Source terms and conditions

## Copyright

Software is legally treated under the Copyright law (together with books and other artistic products). Copyright is intended to protect the original expression of an idea in the form of a creative work, but not the idea itself.
Copyright is a type of intellectual property that gives its owner the exclusive right to copy, distribute, adapt, display, and perform a creative work, usually for a limited time. 

### Example
The C Programming Language First Edition by Dennis Ritchie, Brian Kernighan

![image](https://user-images.githubusercontent.com/126161450/224949750-efe8dd63-bd0f-49e8-95c4-efa3d4c0ed42.png)
 
### Professional consideration
Copyrighted material like excerpts from books or parts of images/songs/software can be published and made available without consent and it’s published copyright and license. This can happen in for instance magazines, web sites or public chat rooms/forums. The absence of a copyright or a license is not equal to it being in the public domain and should be treated as a red flag for usage.

## Public Domain
The public domain consists of all the creative work to which no exclusive intellectual property rights apply. Those rights may have expired, been forfeited, expressly waived, or may be inapplicable. Public domain is a state, or a declaration not comparable with a license, that the legal copyright has expired and thus the work is free to exploit.

### Example
Moby Dick by Herman Melville was first published on October 18th 1851. The copyright for books published in the United States before 1924 has expired why this classic book is in the public domain.

![image](https://user-images.githubusercontent.com/126161450/224949952-4eda7ca1-a9fd-4006-bbae-13c08d8a6781.png)
	 

## Professional consideration
There have been several attempts to prematurely put work in the Public Domain but in legal terms it is uncertain if the Copyright can be avoided. Any professional developer should therefor treat any software with this statement as a very permissive license (e.g. MIT), acknowledging the originator, as no software is yet old enough to be Public Domain.

# Basics of Free Open Source Software Licensing

## Licenses
The author of a developed software is by law the copyright holder of the software unless any separate agreement regulates the copyright ownership.
The copyright holder may decide under what terms and conditions others may use, modify and distribute the open source component. The terms, conditions and obligations for such rights can be stated in a text called the license for the open-source component.
Open-source licenses are licenses that comply with the Open Source Definition — in brief, they allow software to be freely used, modified, and shared. To be approved by the Open Source Initiative (also known as the OSI), a license must go through the Open Source Initiative's license review process.
An open source license can be more or less permissive.
The SPDX License list is sponsored by the Linux Foundation and provides a thorough list of open source licenses with atomized identifiers. The purpose of the list is to enable efficient and reliable identification of the licenses and the exceptions.
Once the copyright holder has provided a developed software under a certain license it can’t be retracted or changed, unless a new version of the software is provided when a new license can be selected.

### Permissive vs non-permissive
The most permissive open source license gives you all freedoms more or less without asking for anything in return. On the other hand, there are licenses requesting you to perform an action for the granted freedoms. These actions can be to inform the end user of the existence of the licensed software in your own product or even make your own developed software available under the same terms as the licensed software you are using it with, also called copyleft.

![image](https://user-images.githubusercontent.com/126161450/224950227-2a8288f9-a6c6-4a9f-8aa1-0907130b53e4.png)
 
* Permissive licenses allow you to copy, modify, recombine, and redistribute the work with minimal restrictions. Usually, only attribution is required. 
* Weak copyleft licenses require that any derivative work, i.e., changed versions of the original open source software, are to be made available under the same license. This requirement does not apply to third party code which is being combined with this software, i.e., the copyleft property does not spread to commercial software.
* Strong copyleft licenses require that the copyleft license is applied to the entire derivative work when a strong copyleft license is combined with other software into a larger software composition. This typically means that proprietary code must be made available under the strong copyleft license. This "contagious" effect creates a commercial risk that the company loses Intellectual Property Rights (IPR) and the investment made in software design.

### Open source license compatibility
The intentions and conditions of different open source licenses can collide, thus developing (with) open source requires consideration on the licenses when including other licensed open source software into your development project.
For instance, including open source software under the Apache v2.0 license while developing under the GPL v3 license is perfectly fine, as long as the end result is released under the GPL v3 license. But, the other way around is not possible. Developing under the Apache v2.0 and including GPL v3 licensed source code if the developed software is to be released under the Apache v2.0 license.

 ![image](https://user-images.githubusercontent.com/126161450/224950604-c5b43183-d907-48bb-ac33-f1bb2f86634f.png)


As stated by the Apache Software Foundation (ASF):
“This licensing incompatibility applies only when some Apache project software becomes a derivative work of some GPLv3 software, because then the Apache software would have to be distributed under GPLv3. This would be incompatible with ASF's requirement that all Apache software must be distributed under the Apache License 2.0.”

### Dual license
The copyright holder may offer the developed software under multiple licenses for the user to choose from when releasing it as an open source software. This is called dual licensing and forces the potential consumer of the open source software to choose which of the offered licenses to comply with. This even includes commercial licensing alternatives which may be more relaxed in terms of obligations and thus possibly more suitable for commercial consumption. 

## Open source license examples

### MIT
The MIT License is a permissive free software license originating at the Massachusetts Institute of Technology (MIT) in the late 1980s. As a permissive license, it puts only very limited restriction on reuse and has, therefore, high license compatibility.
Consuming open source software under the MIT license requires you to include both the license and the copyright in all copies provided. You cannot hold the author liable. Software under the license can be used in commercial development.

### Apache 2.0
The Apache License is a permissive free software license written by the Apache Software Foundation (ASF). It was created 2004 and allows users to use the software with all freedoms, without concern for royalties.
Consuming open source software under the Apache 2.0 license requires you to preserve both the copyright and disclaimer. You cannot hold the author liable. Open source software under this license can be used in commercial development but the license includes a patent grant which assigns a royalty free patent license to all contributions, thereby creating the risk of impacting a contributor's own patents.

### BSD
BSD and BSD-like licenses are permissive free open source software licenses. The original BSD 4-clause license was created 1990 and used by the Berkeley Software Distribution (BSD) which was a Unix-like operating system. The advertising clause of the original version deemed it incompatible with GPL and thereby caused a legal problem. To remedy the situation, the 3-clause version was created in which the advertising clause was removed and is today referred to as the BSD license.
The BSD licenses typically requires you to maintain the copyright, the BSD license notice and a provided disclaimer. There is no requirement to distribute the source code.

### GNU GPL
GNU General Public License is a free open source software license of several versions with a strong copyleft nature. The philosophy behind it is to use the copyright protection to keep open source software free and make any result of software development where it’s included also free. It’s provided by the Free Software Foundation (FSF) which declares the needed four freedoms (to run, study & modify, redistribute exact copies, distribute modified versions) as basis for free open source software. The first version of the license was released in 1989. The latest version (v3) is from 2007.
The GPL licenses requires you to keep the copyright & license and to provide all the source code of your project where the GPL’d software, both original and modified, was included.

### GNU LGPL
The GNU Lesser General Public License is provided by the Free Software Foundation (FSF) to mainly be applied to libraries. It uses the weak copyleft protection to keep any modifications of it free but is more permissive for applications only using the library. Latest version is v3 which was released 2007.
The LGPL licenses typically requires you to keep the copyright & license and to provide the original and any modifications of the source code of the LGPL’d library.

### GNU AGPL
The GNU Affero General Public License is based on the GNU GPL and is thus strong copyleft in its nature but is adopted to handle licensed software executed over a network. Hence, it’s stretching the copyleft principle to apply even for software only accessed over a network. The latest version is v3 and was released 2007.
The AGPL license typically requires you to keep the copyright & license and to provide all the source code of your project where the AGPL’d software was included.

## Non-open source licenses
There are licenses not considered to be open source licenses because of a limitation in any of the granted freedoms. These licenses can look very similar to true open source licenses and can actually be variations of existing open source licenses but with a small change removing a freedom of the licensee.
Non-open source license examples

### Scilab license
The Scilab license doesn’t allow commercial distribution of modified versions of the licensed software and is therefore not considered an open source license.

### Creative Commons CC0 license
The purpose of the creation of the CC0 license by Creative Commons, which was released in 2009, was to provide a tool to waive copyright where jurisdictionally possible or provide a license equivalent to public domain. The license is lacking a clause for patent grant which is why neither FSF or OSI approves it as a free open source license.

## Attribution
Open source attribution typically consist of both copyright notices in the name of the author(s) of the open source software and the open source software license text. For instance, the MIT license requires the notices to be included in all copies of the licensed software.

## Derived work (in relation to license interpretation) 
Derived work is the legal (intellectual property) term for a work that is not independent but arises as a derivative, ‘a new version’ of a previous work (e.g. aggregation, modification, improvement). Think Mona Lisa with moustache or a pregnant Venus. Similarly, to the work it’s based on, the derivative work needs to be original.
Because the derived work needs to be original, it is challenging for software development to understand when a developed solution is merely a logical implementation, given the available syntax and functions provided by the programming language, or it could be considered an original idea. In the latter case, its implementation would reach the necessary threshold for originality, making it copyrightable and hence subject to license terms covering derivative work and those rights.
A fork of an existing open source software for a specific non-general purpose is a good example of a derivative work in the world of software development. The license terms for the original open source software specifies the obligations and needed activities for the fork to fulfil the given rights by the copyright holder.

## Code snippets
According to Wikipedia, a snippet is a programming term for a small region of re-usable source code, machine code, or text.
The snippet needs to be of original content to be considered for copyright protection and doesn’t necessary depend on size, but rather uniqueness and ingenuity. It is not always obvious from the context where you find snippets, that a snippet actually is under copyright protection and was made available under an open source license. For instance, when a snippet is published in a forum like StackOverflow where developers share solutions for various problems with each other.

# Patents
Patents are a separate right that differs from copyright (see sections above), where copyright protects only the specific implementation of an idea, patents could be said to protect the idea itself regardless of its implementation (as long as the specific implementation is covered in the patent claims). As the patent is filed independently from the creation of the code, the copyright owner and the patent owner may well be two different entities. 
It’s not always the case that the patent owner and copyright owner are different entities, in some cases they are one and the same. Even when the same entity holds the patent and the copyright, it need not be the same person that is the inventor and the author. 
When companies use and contribute to open source, potential patent grants in the license needs to be considered. One needs to consider that the patent license can only impact contributors to the open source software. Thus, even if an open source license contains a patent license grant, that does not mean that there are not patents by non-contributors that are applicable and where a separate patent license might be needed.
If using open source under a license that grants patent rights, such as Apache 2.0, one need to consider the scope of such grant to be aware what use it does, and more importantly does not cover. Are the relevant patent holders contributing code to the project, if so, are they contributing code that would necessarily infringe the claims of the patent under consideration? If not, does the license contain any “patent retaliation clause” that would offer “security” to the implementer of the open source software?
If using under a license that does not contain an explicit patent license each organization may have their own policy on how to interpret the lack of an explicit patent license. There is an ongoing legal debate on the topic of “implied patent licenses”. 
When contributing to open source software, an organization needs to consider its own patent portfolio, would a contribution to an open source project “necessarily” infringe their own patent? If so, what license are they contributing under, is the organization willing to agree to those terms? It’s also important to dispel the myth that once the patent has been licensed in one open source project it loses “all value”. The license to the patent granted solely applies to the open source in question, proprietary solutions or even other open source software projects and their downstream users remain unlicensed unless they are reusing the code in question. 
When evaluating if a contribution should be made, it’s important to have a multi stakeholder group to make that decision, IP (such as patents) should be one such consideration, but not the sole consideration, other business aspects need to be considered to form a complete business case to be evaluated.

# Export control

## Introduction
Export Control is a legal term and concerns regulation for the export of goods, software, and technology. Historically, export control started in 1949, with the CoCom organization that formed after WWII as a means to keep technology within the Western alliance. It was replaced in 1994/95 by the Wassenaar Arrangement (WA).
Wassenaar Arrangement is aimed to have a common control of items in the WA control list. All member states must follow these controls. On top of the WA control list, each member state can add other controls through national policies.
Software is export controlled in the following aspects: 
*	Software made exclusively as component of a listed item
*	Software made exclusively for development, production, maintenance, analysis, or use of a listed item
*	Software that emulates the functionality of a listed item
*	Software that is weapon in itself (e.g., intrusion software, viruses, etc.)
*	Software that provides encryption/decryption functionality
Note: US Export controls are Extraterritorial. It means that if the product/software is of “US Origin”, US export regulations must be followed for the product/software where-ever the product is to be exported.

### Criteria / dual use
Any technology with the possibility to be used in both civilian and military purposes is considered as dual use technology and are subject to export control.

### Cryptographic algorithms
The use of cryptographic algorithms to obscure or hide information during transmission is subject to export classification and control.
Cryptographic algorithms are categorized on a scale from very weak to very strong which tend to correlate to how long the algorithm has existed or been in use. The export classification will be more restricted when the encryption is stronger and harder to break.

### Cryptographic algorithms content analysis
To understand the possible export restriction your developed product will have, you need to know what cryptographic algorithms are included and used. This includes both your own developed software and the open source software you included and use.

### Restricted nations
Any country can declare a limitation on interaction with any other country based on its state policy. This might include commercial, cultural or any other type of interaction.
The United States of America is maintaining such a list and requires foreign companies with business in the US to adhere to the restricted nations list maintained by the Office of Foreign Assets Control (OFAC) which is part of the US Treasury Department, Department of State and Bureau of Industry and Security which is a part of the US Department of Commerce.
The European Union (EU) through the European Commission, is also maintaining a list of restricted/sanctioned countries.
United Nations (UN) maintains such lists, and other countries might have lists for other geographic areas/reasons. New lists or updated lists will occur over time.

## Open Source Software as an export controlled item
Open source software is today not export controlled by EU, US, or WA.
The most common open source software that software designers use in a product can in most cases be described as a general, non-exclusive and harmless component that saves time for the designer and money for the company.
With the possible exception of the occasional encryption functionality, open source software is not subject to export control. Nevertheless, a serious export control classification must be made of anything entering a product, and be documented for later reference. Usually, the export control classification of an open source software results in the following: 
•	The manufacturer provides a classification that may be from the Munition List or Dual Use List.
•	The presence of strong encryption code or security protocols classifies it as Dual Use software (5D002).

# Professional implementation examples

## Conveying open source code to third party
Conveyance is an activity which enables a third party to make or receive copies of the open source code as part of license obligation fulfillment either upstream (back to the community/author) or downstream (your customer/public).
Some of the conveyance triggers are: 
•	Stand alone – license trigger for non-modified open source software
•	Derivative work – license trigger for modified open source software

## Making copylefted source code publicly available
When developing software which includes open source code under a copyleft license it is important to mark/take not of what part of the proprietary code base will be affected by the copyleft effect of the open source component in order to have the ability to provide the copylefted source code as part of the license compliance.
There are basically two common approaches to fulfill the license demand of providing the copylefted code base. Either provide the code base as part of your delivery or create an orderable product with an offer, or availability, to download it for free publicly.

## Open source license considerations / general practices
To comply with most of the common open source licenses, a few basic best practices have evolved over the years and is generally recommended: 
1.	Keep the open source code separate from company source code.
2.	Include the original copyright notice in all copies or substantial uses of the work.
3.	Include the original license text with the archived open source software and distributed on any media containing the open source software
4.	 Carry a prominent notice to any changes, stating the change and the company copyright for the change.
5.	Avoid using the name of the original copyright owner to endorse the company product.
6.	State the open source software as included in the company product

To comply with the GPL licenses, it is also recommended to: 
1.	Distribute GPL and LGPL source code as part of the delivered product.
To properly present the fact that the company does not claim Copyright to any open source software, place the following text in a file named LICENSE.txt on all customer delivery media:

_Copyright (C) TheCompany. 
The Software may only be used in accordance with the terms and conditions under which the Software has been supplied. The Software may contain third party software for which the third party's terms and conditions and/or open source software licenses will apply.
License terms, notices, and acknowledgements, if any, for the third party software is found in 3PPLicenses.txt.
_

## Consumption of near-open source licenses
A near-open source license is an open source software license which technically isn’t fulfilling all the freedom requirements of a free open source software license, but doing so in practice.
It should be stated in the company policy documentation if such near-open source software licenses can be used in the product development or not, and what’s needed for such decision to be made.
Similarly, the company policy should state if free open source software licenses that do fulfill all freedom requirements, but isn’t yet approved by OSI/FSF, can be included in the product development. The company policy need also in this case state what’s needed for such decision to be made.
JSON license (an example of a near-open source software license)
The JSON license is based on the Expat license which is based on the permissive MIT license. The JSON license is adding a clause that state “The Software shall be used for Good, not Evil.”. This clause conflicts with “the freedom to run the program as you wish, for any purpose” and is because of that not considered a free open source software license.
