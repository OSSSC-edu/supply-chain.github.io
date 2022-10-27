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

The APT cache is used in order to provide offline information about current packages installed on your system. It essentially guarantees that you are able to access package information without having to be connected to Internet.

![](https://devconnected.com/wp-content/uploads/2019/11/dependencies.png)
**Image source: [https://www.edureka.co/blog/docker-networking/](https://www.edureka.co/blog/docker-networking/)**

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
[Semantic versioning](https://semver.org/) is a popular versioning scheme that is used by many package managers.

## Dependency trees



Transitive dependencies are dependencies of your dependencies.
They are not directly used by your project but they are used by your dependencies.

Direct dependencies are dependencies of your project.
They are directly used by your project.
For example, if you use a library that uses another library, the first library is a direct dependency and the second library is a transitive dependency.

## Dependency resolution mechanisms


https://www.freecodecamp.org/news/javascript-package-managers-101-9afd926add0a#.hu6knvct3

# Software repositories

On Linux, software is distributed through software repositories.
[Software repositories](https://en.wikipedia.org/wiki/Software_repository) are used in order to aggregate free software provided by the community.
Repositories may be tied to a specific distribution.
Ubuntu, Debian, CentOS or RHEL have their own repositories that are updated daily.
As a consequence, when you want to install a new program, you are querying those base repositories in order to retrieve packages from them.
If you wanted to install packages that are not located on distribution based repositories, you would add your own trusted repositories to your system in order to install new packages.

As part of the development lifecycle, source code is continuously being built into binary artifacts using continuous integration. This may interact with a binary repository manager much like a developer would by getting artifacts from the repositories and pushing builds there. Tight integration with CI servers enables the storage of important metadata such as:

- Which user triggered the build (whether manually or by committing to revision control)
- Which modules were built
- Which sources were used (commit id, revision, branch)
- Dependencies used
- Environment variables
- Packages installed

# Software ecosystem

[Software repositories](https://en.wikipedia.org/wiki/Software_repository) is a storage location for software packages.

Package managers are immutable, which leads to natural software diversity.[^1]

Software ecosystems are...[^2]

# Beginner, Normal, Expert Level

# Industry Use Cases

Package managers are designed to eliminate the need for manual installs and updates. 
This can be particularly useful for large enterprises whose operating systems typically consist of hundreds or even tens of thousands of distinct software packages.

# Test your knowledge

## Beginner 👾
- Create a `pom.xml`,  `requirements.txt`, or `packages.json`.
- Create  `Dockerfile`.
- Build a software package from source code.
- Build a container from a `Dockerfile`.

## Expert 💯
- Upload a software package to an external repository.
- Upload a Docker image to Docker Hub.
- Create SBOM

# References

[^1]: Soto-Valero, César, et al. "The emergence of software diversity in maven central." 2019 IEEE/ACM 16th International Conference on Mining Software Repositories (MSR). IEEE, 2019.
[^2]: Decan, Alexandre, Tom Mens, and Philippe Grosjean. "An empirical comparison of dependency network evolution in seven software packaging ecosystems." Empirical Software Engineering 24.1 (2019): 381-416.


