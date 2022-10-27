---
layout: default
title: Package Managers
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

Package managers can be divided intro two categories: system-Level, and development-level.
This section describes the differences between these categories.

A typical use of a package management system is to facilitate the integration of code from possibly different sources into a coherent stand-alone operating unit.
Thus, a package management system might be used to produce a distribution of Linux, possibly a distribution tailored to a specific restricted application.
A package development process, by contrast, is used to manage the co-development of code and documentation of a collection of functions or routines with a common theme, producing thereby a package of software functions that typically will not be complete and usable by themselves.
A good package development process will help users conform to good documentation and coding practices, integrating some level of unit testing.

## System-level package managers

System-level package managers are used to install software on the operating system level.
They are used to install software that is not part of the operating system, but is required for the operating system to function.
For example, the [APT](https://en.wikipedia.org/wiki/APT_(software)) package manager is used to install software on Debian-based Linux distributions.
APT is a command line tool responsible for downloading, installing, updating and removing packages from the local system by communicating with online repositories.

The following figure shows the Linux packaging system:

![](https://devconnected.com/wp-content/uploads/2019/11/linux-packaging-system.png)

For example, the Debian packages repository for the Vim editor is available [here](https://packages.debian.org/stable/editors/vim).
System-level package managers include metadata for each package about what functionalities it provides, who created it but most importantly what packages it depends on.

![](https://devconnected.com/wp-content/uploads/2019/11/dependencies.png)


Below is a list of system-level package managers:

| Package Manager                                                                                              | Description                                                                                                                                                                                              |
|--------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [apt](https://wiki.debian.org/Apt)                                                                           | The Advanced Packaging Tool (APT) is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, Ubuntu and related Linux distributions. |
| [yum](https://en.wikipedia.org/wiki/Yum_(software)) and [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | Package manager for Fedora and Red Hat Enterprise Linux                                                                                                                                                  |
| [Homebrew](https://brew.sh/)                                                                                 | A package installer for MacOS that allows you to install packages Apple didn't                                                                                                                           |

## Development-level package managers

> Development-level packages are essentially one of two things: a library or an application.

The following figure illustrate the use of a package manager to build a software project:

![](./img/package-managers.png)

There are three key elements in the figure: the local repository and the remote repository.
The local repository is the local cache of the package manager.
The remote repository is the remote cache of the package manager.
And the software project is the software project that uses the package manager to manage its dependencies.


| Package Manager                      | Description                                                                                                                                                                                                       |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [npm](https://www.npmjs.com/)        | The Advanced Packaging Tool (APT) is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, Ubuntu and related Linux distributions.          |
| [Maven](https://search.maven.org/)   | The missing package manager for macOS (or Linux).                                                                                                                                                                 |
| [CRAN](https://cran.r-project.org/)  | Yum is a free and open-source command-line package-management utility for computers running Linux operating systems using the RPM Package Manager.                                                                |
 | [RubyGems](https://rubygems.org/)    | The RubyGems package manager is a collection of software development tools that helps you build, install, and manage Ruby applications and libraries.                                                             |
 | [NuGet](https://www.nuget.org/)      | NuGet is the package manager for .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers. |
 | [Pip](https://pypi.org/)             | The Python Package Index (PyPI) is a repository of software for the Python programming language.                                                                                                                  |
 | [Cargo](https://crates.io/)          | Cargo is the Rust package manager.                                                                                                                                                                                |
 | [Go](https://golang.org/)            | Go is an open source programming language that makes it easy to build simple, reliable, and efficient software.                                                                                                   |
 | [Bower](https://bower.io/)           | A package manager for the web.                                                                                                                                                                                    |
 | [Composer](https://getcomposer.org/) | Dependency Manager for PHP                                                                                                                                                                                        |
 | [Yarn](https://yarnpkg.com/)         | Fast, reliable, and secure dependency management.                                                                                                                                                                 |
 | [Pub](https://pub.dev/)              | Pub is the package manager for the Dart programming language, containing reusable libraries & packages for Flutter, AngularDart, and general Dart programs.                                                       |
 | [CPAN](https://www.cpan.org/)        | The Comprehensive Perl Archive Network (CPAN) is a repository of software for the Perl programming language.                                                                                                      |



## Deployment-level package managers

| Package Manager                                      | Description                                                                                                                                                                                              |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Docker Hub](https://hub.docker.com/                 | The Advanced Packaging Tool (APT) is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, Ubuntu and related Linux distributions. |
| [Docker Registry](https://docs.docker.com/registry/) | The missing package manager for macOS (or Linux).                                                                                                                                                        |
| [Quay](https://quay.io/)                             | Yum is a free and open-source command-line package-management utility for computers running Linux operating systems using the RPM Package Manager.                                                       |
| [GitHub Container Registry]()                        | TODO                                                                                                                                                                                                     |


# Dependencies

The dependency code constitutes your dependencies. 
It shouldn’t be mutated during the lifetime of your application, and should be accessible by your project code in memory when it’s needed.

## Versioning

## Dependency trees

Transitive dependencies are dependencies of your dependencies.
They are not directly used by your project but they are used by your dependencies.

Direct dependencies are dependencies of your project.
They are directly used by your project.
For example, if you use a library that uses another library, the first library is a direct dependency and the second library is a transitive dependency.

## Resolution mechanism


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

# Test Questions

## Beginner
Create a POM xml, etc.
Create a requirements.txt

## Expert
Create SBOM
Run some tools

# References

[^1]: Soto-Valero, César, et al. "The emergence of software diversity in maven central." 2019 IEEE/ACM 16th International Conference on Mining Software Repositories (MSR). IEEE, 2019.
[^2]: Decan, Alexandre, Tom Mens, and Philippe Grosjean. "An empirical comparison of dependency network evolution in seven software packaging ecosystems." Empirical Software Engineering 24.1 (2019): 381-416.


