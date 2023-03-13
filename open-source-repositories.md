---
layout: default
title: OSS Repositories
parent: Fundamentals
nav_order: 1
---

# OSS Repositories
A software project is composed of multiple artifacts, such as its source code and tests, the documentation, as well as configuration and installation scripts. If the artifacts of a software project are available publicly, to read and modify, the software is said to be __open-source__. Software projects across all domains, such as [email clients](https://gitlab.gnome.org/GNOME/evolution), [e-commerce platforms](https://github.com/spree/spree), [video games](https://mindustrygame.github.io/), [web browsers](https://firefox-source-docs.mozilla.org/), [space-robot](https://github.com/nasa/astrobee) software, programming [languages](https://github.com/Rick-Lang/rickroll-lang), and even whole [operating system kernels](https://github.com/torvalds/linux), may be free and open-source ([FOSS](https://en.wikipedia.org/wiki/Free_and_open-source_software)). Millions of software projects are hosted as code repositories on online platforms such as [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/), and [SourceForge](https://sourceforge.net/directory/), to name a [few](https://en.wikipedia.org/wiki/Comparison_of_source-code-hosting_facilities). A code repository is the place where contributors work, exchange, discuss and collaborate.

As an example, let us consider the [widely-used](https://xkcd.com/1823/), open-source text editor called [Vim](https://en.wikipedia.org/wiki/Vim_(text_editor)). Vim is freely available through its [repository on GitHub](https://github.com/vim/vim). In addition to the actual code that powers Vim, this repository also showcases a comprehensive introduction to this software project. The repository documents how Vim can be built from the source code, guidelines for how individuals can contribute, as well as statistics such as the major programming languages that Vim is implemented in. Much like this repository, the [`README` file](https://en.wikipedia.org/wiki/README), is usually a very good place to start when first learning about an open-source project. The contents of the `README` file within each directory of a project are automatically displayed when browsing through its repository. This is also the case for the feature-rich and powerful [Inkspace](https://en.wikipedia.org/wiki/Inkscape) vector image editing tool, hosted as an open-source [repository on GitLab](https://gitlab.com/inkscape/inkscape).

Regardless of the specific platform where an open-source project is hosted, browsing through its repository can be an informative and rather fun exercise. It allows us to gain insights into how the project has evolved with time, issues and bugs that have been discovered, those that have been resolved, as well as code contributions made by the open-source community. Moreover, we also learn about other open-source technologies that power the project, which opens up more avenues for [exploration](https://github.com/explore).

### _Outline_ 📋
In this chapter, we learn about
- How individuals [contribute](#contributors) to open-source projects
- How we can guage the [activity and popularity](#activity-and-popularity) of open-source projects
- Open-source [licenses](#licenses)
- [Versioning](#versioning) in open-source software systems
- [Use cases](#industry-use-cases) for open-source software in the industry

We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in the [references](#references). 

## Contributors
A software project typically has multiple contributors. There are various ways in which an individual may contribute to a software project, such as with the implementation of a new feature, to fix a bug, with a new test that verifies an untested behavior, or to improve the documentation, including [translations](https://github.com/chrislgarry/Apollo-11) to spoken languages. The open-source movement thrives (see reference [1](#ref_1)) as a direct consequence of the contributions made by enthusiasts, users, and developers, who have diverse backgrounds and areas of expertise, and come from different geographical regions.

Open-source software projects maintain a list of individuals who have contributed to them. An individual becomes a contributor to a software project when a submission made by them is adopted into the code-base of the project. The number of contributors of a software project can be useful to guage the [maturity](https://en.wikipedia.org/wiki/Linus%27s_law) of an open-source software project. For example, the [node](https://github.com/nodejs/node) project repository lives on GitHub, and has received contributions from thousand of individual contributors. Incoming contributions to the project are presented on the the [pull requests tab](https://github.com/nodejs/node/pulls). We can also investigate the history of contributions more deeply through the [contributors page](https://github.com/nodejs/node/graphs/contributors), which indicates the developers most actively involved in the project. 

## Activity and Popularity
A majority of open-source projects today use a distributed versioning system called [Git](https://en.wikipedia.org/wiki/Git), including all the projects hosted on prominent platforms such as GitHub and GitLab. Git is a handy tool with many features that facilitate efficient collaboration among the contributors of a software project. A developer can submit changes to a project incrementally via __commits__, which are atomic units of contribution in the Git workflow. Git is an essential prerequisite to understanding and contributing to open-source projects. Many excellent resources exist online that introduce its foundations, as well as more advanced usage (see references [2](#ref_2) and [3](#ref_3)). The source code of Git itself resides in a [GitHub repository](https://github.com/git/git), where we can observe the project, including the [latest commits](https://github.com/git/git/commits/master) to its main development branch. As a rule of thumb, more actively developed and maintained open-source projects have more frequent and recent commits.

In addition to the commits, some more metrics can indicate the popularity of an open-source project. For example, a user can follow the updates made to a project on GitHub by starring its repository, and receive notifications by watching it. Users may also create a copy, or fork, of the project in order to implement some of their own extensions to it, and optionally contribute them back to the original project through pull requests.

![](./img/activity-popularity.png)

In the figure above, we see the GitLab repository of the [Tezos](https://gitlab.com/tezos/tezos) blockchain, and the GitHub repository of the [MongoDB](https://github.com/mongodb/mongo) database. For both projects, we see the number of commits, as well as the number of times they have been starred and forked by users. 

## Licenses
Most open-source projects include a [license](https://en.wikipedia.org/wiki/Open-source_license), which is a legal document that defines the terms in which the use of the software is permitted. It also tells the users of the software what their rights are, with respect to the software. For example, the license dictates if a software project may be incorporated only in non-commercial contexts or even in commercial products, used directly without being modified, or may be customized before being used, etc. It is useful to [compare](https://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licenses) between the many available open-source licenses and [choose](https://choosealicense.com/) one that is right for a project. The license is usually specified in a file called `LICENSE`, as in the case of the [NASA worldview](https://github.com/nasa-gibs/worldview/blob/main/LICENSE.md) project.

## Versioning
In order to keep track of incremental changes in a software project repository, Git assigns unique identifiers to a snapshot of the state of the project at each commit. For example, [astropy](https://github.com/astropy/astropy) is a library that provides tools to work with astronomical data in the [Python language](https://en.wikipedia.org/wiki/Python_(programming_language)). Each [commit](https://github.com/astropy/astropy/commits/main) in astropy has its own __commit id__, as well as a brief description, or __commit message__, of the changes it includes.

Developers mark important milestones in their software project as it evolves with time. This is achieved by assigning __versions__ to the state of the project at a certain point in time. If a developer fixes an important [bug](https://en.wikipedia.org/wiki/Software_bug) or implements a new feature, a new [version](https://semver.org/) of the software is released. A new version is the culmination of smaller changes, such as multiple commits. It is good practice to [document the changes](https://keepachangelog.com/en/1.0.0/) included within a new version, so that users of the software are aware of them.




## DIY
Find two open-source projects, and report the following data for them:
### _Novice_ 👾
- Name
- Organisation
- Domain
- Link to the project repository
- Main programming language(s)
- Number of commits
- Link to the most recent commit
- License
- Other interesting statistics / information (recent activity, contributors, stars, ...)

### _Expert_ 💯
- A bug report
- A contribution accepted into the project
- A file with source code
- A file with test code
- Latest release
- Personal experiences using / working with the project
- Mentions on Wikipedia / in the press
- Project website

## References
1. <a name="ref_1">[Pots of Gold at the End of the Rainbow: What is Success for Open Source Contributors?](https://ieeexplore.ieee.org/document/9524493)</a>
2. <a name="ref_2">[The Git Book](https://git-scm.com/book/en/v2)</a>
3. <a name="ref_3">[Learn Git Branching](https://learngitbranching.js.org/)</a>
4. <a name="ref_4">[The Multibillion Dollar Software Supply Chain of Ethereum](https://arxiv.org/abs/2202.07029)</a>
