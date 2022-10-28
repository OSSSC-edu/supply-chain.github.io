---
layout: default
title: Package managers
nav_order: 2
description: "This chapter describes the use of package managers in software development"
permalink: /package-managers
---

# Package managers

[Package managers](https://en.wikipedia.org/wiki/Package_manager) are software tools that allow to handle software dependencies in a consistent manner.
Most package managers are used to automate the process of installing, upgrading, configuring, and removing third-party [software dependencies](https://en.wikipedia.org/wiki/Third-party_software_component).
They also provide a consistent interface for installing software across different operating systems and distributions.
This chapter describes the use of package managers in software development.

# Categories

Package managers can be divided into three categories: system-level, deployment-level, and development-level.
This section describes the differences between these categories.

## System-level package managers

System-level package managers are used to install software on the operating system level.
They are used to install software that is not part of the operating system, but is required for the operating system to function.
For example, the [APT](https://en.wikipedia.org/wiki/APT_(software)) package manager is used to install software on Debian-based Linux distributions.
APT is a command line tool responsible for downloading, installing, updating and removing packages from the local system by communicating with online repositories.

The following figure shows the Linux packaging system:

![](https://devconnected.com/wp-content/uploads/2019/11/linux-packaging-system.png)
**Image source: [https://devconnected.com/apt-package-manager-on-linux-explained/](https://devconnected.com/apt-package-manager-on-linux-explained/)**

For example, the Debian packages repository for the Vim editor is available [here](https://packages.debian.org/stable/editors/vim).
System-level package managers include metadata for each package about what functionalities it provides, who created it but most importantly what packages it depends on.

The APT cache is used in order to provide offline information about current packages installed on your system. 
It essentially guarantees that you are able to access package information without having to be connected to Internet.

![](https://devconnected.com/wp-content/uploads/2019/11/dependencies.png)

**Image source: [https://devconnected.com/apt-package-manager-on-linux-explained/](https://devconnected.com/apt-package-manager-on-linux-explained/)**

Below is a list with some of the most popular package managers for different operating systems:

| Package Manager                                                                                             | Description                                                                  |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| [apt](https://wiki.debian.org/Apt)                                                                          | The package manager for Debian, Ubuntu and related free Linux distributions. |
| [yum](https://en.wikipedia.org/wiki/Yum_(software)) and [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | The package manager for Fedora and Red Hat Enterprise Linux distributions.   |
| [Mac App Store](https://en.wikipedia.org/wiki/Mac_App_Store)                                                | The package manager for macOS applications.                                  |
| [Google Play](https://en.wikipedia.org/wiki/Google_Play)                                                    | The package manager for Android applications.                                |
| [Windows Package Manager](https://en.wikipedia.org/wiki/Windows_Package_Manager)                            | The package manager for Windows.                                             |

## Deployment-level package managers

Deployment-level package managers are used to handle container images and application dependencies. 
They are used to install software that is required for the application to function in a standalone manner without dependence on the operative system.
For example, [Docker](https://en.wikipedia.org/wiki/Docker_(software)) package manager is used to install software in a containerized environment, and [Docker Hub](https://hub.docker.com/) is is a cloud-based repository that allows users to create, manage, and store these container images.
Docker provides an interface to communicat with Docker Hub and deploy images there.
These images are uploaded onto the Docker Hub(Git repository for Docker Images) which contains public/private repositories.

The following figure illustrates how the Docker packaging system operates on a network:
![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/Picture1-1.png)
**Image source: [https://www.edureka.co/blog/docker-networking/](https://www.edureka.co/blog/docker-networking/)**

So, from public repositories, you can pull your image as well and you can upload your own images onto the Docker Hub.
Then, from Docker Hub, various teams such as Quality Assurance or Production teams will pull that image and prepare their own containers.
These individual containers, communicate with each other through a network to perform the required actions, and this is nothing but Docker Networking.
Docker Networking as a communication passage through which all the isolated containers communicate with each other in various situations to perform the required actions.

| Package Manager                                                                                                                              | Description                                                                                                                                                                     |
|----------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Docker Hub](https://hub.docker.com/)                                                                                                        | Docker Hub is the world's largest library and community for container images                                                                                                    |
| [Docker Registry](https://docs.docker.com/registry/)                                                                                         | The Registry is a stateless, highly scalable server side application that stores and lets you distribute Docker images.                                                         |
| [Quay](https://quay.io/)                                                                                                                     | Quay is a package manager from RedHat that builds, analyzes, and distributes container images                                                                                   |
| [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry) | A package manager from GitHub that that allows to store and manage Docker and OCI images in the Container registry, which uses the package namespace [ghcr.io](https://ghcr.io) |

## Development-level package managers

Development-level package managers run on top of the operative system and operate on top of the programming language tools that developers use to build software applications.
In contrast with system-level package managers, development-level package managers focus on a small part of the software system, such as a programming language or a framework.
They are used to manage the co-development of code and documentation of a collection of functions or routines with a common theme, producing thereby a package of software functions that typically will not be complete and usable by themselves.
A good package development process will help users conform to good documentation and coding practices, integrating some level of [unit testing](https://en.wikipedia.org/wiki/Unit_testing).

> Development-level packages are essentially one of two things: a [library](https://en.wikipedia.org/wiki/Library_(computing)) or an [application](https://en.wikipedia.org/wiki/Application_software).

The following figure illustrates the typical use of a package managers to build a software project:

![](./img/package-managers.png)

There are three key elements in the figure: the local repository and the remote repository.
The local repository is the local cache of the package manager.
The remote repository is a remote address on the internet where the dependencies are hosted.
The software project is the software project that uses the package manager to manage its dependencies.

If authors are allowed to remove their packages from the ecosystem, this increases the risk of breaking (transitive) dependents upon package removal.
Therefore, most development-level package managers today are immutable, which means that dependencies cannot be changed once they are deployed.[^1]
This means that if a dependency is found to have a bug, the only way to fix it is to release a new version of the dependency.
The immutable nature of package managers is a key feature that allows for reproducible builds.

> A famous example of the problem with mutable package managers is the left-pad incident for the npm package manager. 
> Despite its small size (just a few lines of source code), the sudden and unexpected removal of the left-pad package caused thousands of direct and indirect dependent projects to break, including very popular ones such as `Atom` and `Babel`.

Below is a list with some of the most popular package managers for different programming languages:

| Package Manager                      | Description                                                                                                                                                                                                       |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [npm](https://www.npmjs.com/)        | The Advanced Packaging Tool (APT) is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, Ubuntu and related Linux distributions.          |
| [Pip](https://pypi.org/)             | The Python Package Index (PyPI) is a repository of software for the Python programming language.                                                                                                                  |
| [Maven](https://search.maven.org/)   | The missing package manager for macOS (or Linux).                                                                                                                                                                 |
| [CRAN](https://cran.r-project.org/)  | Yum is a free and open-source command-line package-management utility for computers running Linux operating systems using the RPM Package Manager.                                                                |
| [RubyGems](https://rubygems.org/)    | The RubyGems package manager is a collection of software development tools that helps you build, install, and manage Ruby applications and libraries.                                                             |
| [NuGet](https://www.nuget.org/)      | NuGet is the package manager for .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers. |
 | [Cargo](https://crates.io/)          | Cargo is the Rust package manager.                                                                                                                                                                                |
 | [Composer](https://getcomposer.org/) | Dependency Manager for PHP                                                                                                                                                                                        |

# Software Dependencies

Software dependencies are the components of a software system that are not part of the system itself, but are required for the system to function.
In development environments, software dependencies are typically pulled from software repositories at build time.

These are the characteristics of software dependencies:

1. They are not part of the software system itself.
2. They are required for the system to function.
3. They are typically pulled from software repositories at build time.
4. They are typically managed by a package manager.
5. They are typically versioned.

Software dependencies are an important part of software development.
A key aspect to consider is how they are handled by the package manager.
Every package manager has a different way of handling dependencies.
For example, some package managers will automatically pull the dependencies of a package to a local filesystem, while others will not.
Some package managers will automatically update the dependencies of a package, while others will not.
Dependency resolution mechanisms and dependency updates are important aspects to consider when choosing a package manager.

## Versioning

Dependency versioning is a mechanism that allows to specify the version of a dependency that is required by a software project.
This is important because it allows to handle the case where a dependency is updated and the software project is not compatible with the new version of the dependency.
The Semantic Versioning Specification ([SemVer](https://semver.org/)) is a popular versioning scheme that is used by many package managers.

## Dependency trees

Dependency trees are a way to represent the dependencies of a software project.
A dependency tree is a graph where the nodes are the dependencies of a software project and the edges are the dependencies between the nodes.
Package managers typically use dependency trees to manage the dependencies of a software project.

In a dependency tree there are three main types of nodes:

1. The root node is the software project itself.
2. Direct dependencies are the dependencies of the root node that are declared in .
3. Transitive dependencies are dependencies of the direct dependencies.

Transitive dependencies deserve special attention as they are not directly used by your project but they are used by your dependencies.
For example, if you use a library that uses another library, the first library is a direct dependency and the second library is a transitive dependency.

The following figure shows the dependency tree of the project `com.github.ferstl` as resolved by the Maven package manager:

![](https://github.com/ferstl/depgraph-maven-plugin/raw/master/src/doc/by-group-id.png)
**Image source: [https://github.com/ferstl/depgraph-maven-plugin/raw/master/src/doc/by-group-id.png](https://github.com/ferstl/depgraph-maven-plugin/raw/master/src/doc/by-group-id.png)**

As you observe, the root node is the project `com.github.ferstl`.
The direct dependencies are the projects `commons-codec`, `org.apache.commons`, `junit`, `com.google.guava`, `org.springframework`, and `com.mysema.querydsl`.
The transitive dependencies are `org.hamcrest`, `com.google.code.findbugs`, `com.mysema.commons`, and `com.infradna.tool`.

## Dependency resolution mechanisms

Dependency resolution mechanisms are protocols that package managers use to determine which are the dependencies in the dependency tree of a software project.
Different package managers use different dependency resolution mechanisms.
In particular, these mechanism allows to resolve conflicts between dependency versions.
This is because, in most package managers, only one version of any particular package can be installed at a time.
In that sense, one of the package manager’s primary responsibilities is to figure out a set of package versions that will satisfy every version constraint simultaneously.

> “**Dependency hell**” is a colloquial term denoting the frustration resulting from the inability to install software due to complicated dependencies.[^3] 

For example, the Maven package manager relies on a [dependency resolution mechanism](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html) that determines which version of a dependency to use based on the proximity of the dependency to the root node.
On the other hand, the npm package manager uses a [dependency resolution mechanism](https://medium.com/learnwithrahul/understanding-npm-dependency-resolution-84a24180901b) that attempts to flatten the dependency tree as much as possible whereas picking the version based on the installation order expressed in the `package.json` file.

# Software repositories

[Software repositories](https://en.wikipedia.org/wiki/Software_repository) is a storage location for software packages.
They are used in order to aggregate free software provided by the community.

For example, on Linux, software is distributed through software repositories.
Repositories may be tied to a specific distribution.
Ubuntu, Debian, CentOS or RHEL have their own repositories that are updated daily.
As a consequence, when you want to install a new program, you are querying those base repositories in order to retrieve packages from them.
If you wanted to install packages that are not located on distribution based repositories, you would add your own trusted repositories to your system in order to install new packages.

As part of the development lifecycle, source code is continuously being built into binary artifacts using continuous integration. 
This may interact with a binary repository manager much like a developer would by getting artifacts from the repositories and pushing builds there. 
Tight integration with CI servers enables the storage of important metadata such as:

- Which user triggered the build (whether manually or by committing to revision control)
- Which modules were built
- Which sources were used (commit id, revision, branch)
- Dependencies used
- Environment variables
- Packages installed

# Software ecosystems

Software ecosystems are Large collections of interdependent software components, including package managers, that are maintained by large and geographically distributed communities of collaborating contributors.[^2]
Typical examples of open source software ecosystems are distributions for Linux operating systems and packaging ecosystems for specific programming languages.
Each package manager has its own polices related to package updates or package dependencies
While packaging ecosystems are extremely useful for their respective communities of developers, they face challenges related to their scale, complexity, and rate of evolution. 
Typical problems are backward incompatible package updates, and the risk of (transitively) depending on packages that have become obsolete or inactive.
Assessing the quality of package dependency networks, and supporting it through proper dependency management tools, better policies, and ecosystem health analysis dashboards is becoming of utmost importance.

To address this issue, the “[software bill of materials](https://www.cisa.gov/sbom)” (SBOM) has emerged as a key building block in software security and software supply chain risk management. 
A SBOM is a nested inventory, a list of ingredients that make up software components.
In a nutshell, a SBOM is formal and machine-readable metadata that uniquely identifies a software package and its contents.
It may include other information about its contents, including copyrights and license data.
SBOMs are designed to be shared across organizations and are particularly helpful at providing transparency of components delivered by participants in a software supply chain. 
Many organizations concerned about software security are making SBOMs a cornerstone of their cyber-security strategy.[^4]

# Industry Use Cases

Package managers are designed to eliminate the need for manual installs and updates. 
This can be particularly useful for large enterprises whose operating systems typically consist of hundreds or even tens of thousands of distinct software packages.
For example, consider a bank that has a large number of servers running Linux and that needs to install a new package on all of them.
Without a package manager, the bank would need to manually download the package, install it, and then repeat the process for every server.
With a package manager, the bank can simply run a single command to install the package on all of its servers.

On the other hand, there is a lot of interest from companies in learning about the “health” of open-source components.[^2]
This implies learning about the components of their direct and transitive dependencies.
Companies know that the health of a single component depends on the health of the ecosystem in which it is produced and used.
From the point of view of people producing software, they want to track everything around them. 
Just as a single example, they need to know if modules on which their software depend are healthy or not.
From the point of view of users, that happens as well.
For example, to understand the security problems of a product, they need to understand the security problems of all its dependencies, and in many cases, of their transitives developed by the same community.

# Test your knowledge

## Beginner 👾
- Create a `pom.xml`,  `requirements.txt`, or `packages.json`.
- Create  `Dockerfile`.
- Build a software package from source code.
- Build a container from a `Dockerfile`.

## Expert 💯
- Upload a software package to an external repository.
- Upload a Docker image to Docker Hub.
- Create SBOM.

# References

[^1]: Soto-Valero, César, et al. "The emergence of software diversity in maven central." 2019 IEEE/ACM 16th International Conference on Mining Software Repositories (MSR). IEEE, 2019.
[^2]: Decan, Alexandre, Tom Mens, and Philippe Grosjean. "An empirical comparison of dependency network evolution in seven software packaging ecosystems." Empirical Software Engineering 24.1 (2019): 381-416.
[^3]: Abate, Pietro, et al. "Dependency solving is still hard, but we are getting better at it." 2020 IEEE 27th International Conference on Software Analysis, Evolution and Reengineering (SANER). IEEE, 2020.
[^4]: [Software Bill of Materials (SBOM) and Cybersecurity Readiness](https://www.linuxfoundation.org/research/the-state-of-software-bill-of-materials-sbom-and-cybersecurity-readiness)


[//]: # (Pipreqs is a tool that can generate a requirements.txt file containing the list of a project’s dependencies and their versions based on imports that it detects in the source code.)

[//]: # ()
[//]: # (```shell)

[//]: # ($ pip install <packagename>)

[//]: # (```)

[//]: # ()
[//]: # (Pipreqs)

[//]: # ()
[//]: # (Pipreqs is a tool that can generate a requirements.txt file containing the list of a project’s dependencies and their versions based on imports that it detects in the source code.)

[//]: # (Pipreqs Usage)

[//]: # ()
[//]: # (To install pipreqs, enter:)

[//]: # ()
[//]: # (```shell)

[//]: # ($ pip install pipreqs )

[//]: # (```)

[//]: # ()
[//]: # (To generate a requirements.txt file, enter:)

[//]: # ()
[//]: # (```shell)

[//]: # ($ pipreqs /<projectlocation>)

[//]: # (  # requirements.txt)

[//]: # (  pkginfo==1.5.0.1)

[//]: # (  tabulate==0.8.7)

[//]: # (  structlog==20.1.0 )

[//]: # (  ...)

[//]: # (```)