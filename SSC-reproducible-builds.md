---
layout: default
title: Reproducible Builds
parent: OSS Supply Chain
nav_order: 1
---

# Reproducible Builds

[Reproducible builds](https://reproducible-builds.org/docs/) are a set of software development practices that create an independently verifiable path from
source to binary code.
A build is reproducible if given the same source code, build environment and build instructions, any party can recreate bit-by-bit identical copies of all
specified artifacts.
This build methodology allows verifying that no vulnerabilities or backdoors have been introduced in the supply chain.
Notice that to achieve reproducible builds, the CI/CD system needs to be made entirely deterministic: modifying a given source must always create the same
result.
For example, the current date and time must not be recorded and outputs always have to be written in the same order.
Furthermore, the set of tools used to perform the build and, more generally, the building environment should either be recorded or pre-defined.
Developers should have a way to recreate a close enough build environment, perform the build process, and validate that the output matches the original build.

In this scenario, users can establish trust in free and open-source software (FOSS) executables by following the process shown in the following figure from Lamb
et. al.[^1] Software development occurs upstream, and the source code is then distributed to downstream vendors such as Linux distributions and app stores. These vendors build
binaries from the source code and distribute them to end-users. It is important to note that neither the distribution process nor the build process can be
completely trusted in this scenario, as they are subject to potential threats in the real world.

![](/img/reproducible-builds.png)

In the figure: the reproducible builds approach to increasing trust in executables built by untrusted third parties.
The end-user should reject the binary artifact from their software vendor, as its checksum (`0xBAAD`) does not
match the one built by multiple, independent third-parties (`0x1337`).

### _Outline_ 📋

In this chapter, we learn about:

- The [benefits of setting up reproducible builds](#benefits-of-reproducible-builds)
- A real-world example of a [system that employs reproducible builds](#example--the-gnulinux-os)
- Popular [tools](#tools) to help you achieve reproducible builds.

We also encourage you to explore the links throughout the text, the [Do-It-Yourself](#diy) tasks, as well as the resources listed in
the [references](#references).

## Benefits of Reproducible Builds

There are several benefits to reproducible builds in software development.
Having reproducible builds is important because it allows developers to ensure the integrity and security of their software, and it allows users to verify that
the
software they are using has not been tampered with.

One benefit is that it helps to ensure the integrity of the software.
When a build is reproducible, it means that anyone who has access to the source code and build instructions can recreate the build and verify that it is the
same as the original.
This can help to prevent tampering or the inclusion of malicious code in the software.

Another benefit of reproducible builds is that it allows developers to more easily identify and fix bugs in their software.
When a build is reproducible, it means that developers can reproduce the build on their own systems in order to debug and troubleshoot any issues that may
arise.
This can save time and effort compared to trying to recreate a build from scratch or relying on users to report issues with the software.

Reproducible builds can also help to improve the security of software.
When a build is reproducible, it means that users can verify that the software they are using has not been tampered with or modified in any way.
This can be especially important for software that is used in critical infrastructure or other sensitive applications, such as industrial control systems,
transportation systems, or communication systems.[^2]

There are several factors that can affect the reproducibility of a build.[^3]
One factor is the use of [external dependencies](package-managers.md#software-dependencies), such as libraries or other software that is included in the build.
If these dependencies are not properly managed and controlled, it can be difficult to reproduce the build.
Another factor is the build environment, including the operating system, compilers, and other tools used to create the build.
If the build environment is not consistent, it can be difficult to reproduce the build.[^5]

In order to create reproducible builds, developers can follow a number of best practices.
These can include using version control systems to manage the source code and build instructions, using consistent build environments, and properly managing
external dependencies.
It can also be helpful to use automated tools and processes to ensure the reproducibility of builds.

Overall, reproducible builds are an important aspect of software development that can help to ensure the integrity and security of software, as well as improve
the reliability and maintainability of the software over time.
By following best practices for reproducible builds, developers can create software that is more trustworthy and can be more easily verified and reproduced by
other parties.

## Example: The GNU/Linux OS

One example of a system that employs reproducible builds is the GNU/Linux operating system.
The GNU/Linux operating system is a free and open-source operating system that is used on a wide range of devices, including servers, desktop computers, and
embedded systems.

The GNU/Linux operating system is built using a process called [cross-compilation](https://www.linkedin.com/pulse/what-cross-compilation-loutfi-belaaribi/),
which allows developers to build the operating system on one platform (such as a desktop computer) and then run it on another platform (such as an embedded
system).
This process relies on reproducible builds in order to ensure the integrity and security of the operating system.

To create reproducible builds of the GNU/Linux operating system, developers follow a set of best practices that are outlined in [The GNU Reproducible Builds
Project](https://www.gnu.org/software/mes/manual/html_node/Reproducible-Builds.html).
These practices include using version control systems to manage the source code and build instructions, using consistent build environments, and properly
managing external dependencies.

In addition, the GNU/Linux operating system uses a variety of automated tools and processes to ensure the reproducibility of builds.
For example, the operating system includes a tool called [diffoscope](https://diffoscope.org/) that can compare two builds and identify any differences between
them.
This tool can be used to verify that two builds are identical and thus reproducible.

Overall, the GNU/Linux operating system is an example of a system that relies on reproducible builds in order to ensure the integrity and security of the
software.
By following best practices for reproducible builds and using automated tools and processes, the developers of the GNU/Linux operating system are able to create
software that is more trustworthy and can be more easily verified and reproduced by other parties.

## Tools

There are several tools that can be used to create reproducible builds, depending on the specific needs and requirements of the software project.
Some common tools that are used for this purpose include:

- Version control systems: Version control systems, such as Git or Subversion, are used to manage the source code and build instructions for a software project.
  These systems allow developers to track changes to the codebase, revert changes if necessary, and collaborate with other developers.
  By using a version control system, developers can ensure that the source code and build instructions are well-organized and easily accessible, which can help
  to make builds more reproducible.

- Build automation tools: Build automation tools, such as Make or Maven, are used to automate the build process for software projects.
  These tools allow developers to specify the steps required to build the software and then execute those steps automatically.
  By using a build automation tool, developers can more easily reproduce builds and ensure that the build process is consistent and reliable.

- Package managers: Package managers, such as npm or pip, are used to manage external dependencies for a software project.
  These tools allow developers to easily install and update the libraries and other software dependencies that are needed to build the software.
  By using a package manager, developers can more easily manage external dependencies and ensure that builds are reproducible.

- Continuous integration tools: Continuous integration tools, such as [Jenkins](https://www.jenkins.io/) or [CircleCI](https://circleci.com/), are used to
  automate the build and test process for software
  projects.
  These tools allow developers to automatically build and test the software whenever changes are made to the codebase.
  By using a continuous integration tool, developers can more easily ensure that builds are reproducible and that the software is working as expected.

There are many language-specific tools that can be used to create reproducible builds, and the specific tools that are used will depend on the needs and
requirements of
each project.
For example, the [Reproducible Build Maven Plugin](https://zlika.github.io/reproducible-build-maven-plugin/) is a popular Java Maven tool used to ensure that a
Maven
build is reproducible, meaning that it produces the same artifact (e.g., JAR file) every time it is run with the same input.
The plugin works by generating a checksum for each file that is included in the build, and then comparing those checksums to the checksums of the same files in
a reference build. If the checksums match, then the build is considered reproducible. If the checksums do not match, then the plugin will report an error and
the build will fail. To use the plugin, developers simply need to include it in their Maven build configuration file (i.e., `pom.xml`).

By using the right tools and following best practices for reproducible builds, developers can create software that is more trustworthy and can be more easily
verified and reproduced by other parties.

## EBuild Configuration Files

The following configuration file is an example that specifies the tools and settings that will be used to create a reproducible build of the software.
The file specifies the version control system, build automation tool, package manager, and continuous integration tool that will be used, as well as the build
environment and the dependencies for the build.
It also includes instructions for building, testing, and releasing the software.

```bash
# Configuration file for a reproducible build

# Set the version control system to use
version_control_system = git

# Set the build automation tool to use
build_automation_tool = make

# Set the package manager to use
package_manager = pip

# Set the continuous integration tool to use
continuous_integration_tool = Jenkins

# Set the build environment
build_environment =
  operating_system = Linux
  compilers = gcc, g++
  build_tools = make

# Set the dependencies for the build
dependencies =
  - library1
  - library2
  - library3

# Set the build instructions
build_instructions =
  - make clean
  - make build
  - make test
  - make install

# Set the test instructions
test_instructions =
  - make test

# Set the release instructions
release_instructions =
  - make release
```

## Challenges

There are several challenges that can affect the reproducibility of a build.[^6]
In order to achieve reproducible builds, it is important to ensure that the build system is deterministic. This means that given the same source code, the build
process should always produce the same result. To accomplish this, it is necessary to avoid recording the current date and time and to ensure that output is
always written in the same order. Additionally, the tools used to perform the build and the build environment should be recorded or pre-defined, and users
should have the ability to recreate a similar build environment, perform the build, and validate that the output matches the original build. Some of the
challenges in achieving reproducible builds include managing the complexity of the build environment, ensuring that all necessary dependencies are recorded or
pre-defined, and verifying that the build process produces consistent results.

A common question related to reproducible builds is how is it possible to know if the build environment is not compromised if everyone is using the same
binaries? Or how can I trust that the compiler I just built was not compromised by a backdoor in the compiler I used to build it?[^7]
The technique known as diverse double-compilation can answer this question.[^8] Given two compilers, one trusted and one under test, the compiler under test is
built twice, once with each compiler. Using the compilers created from
this build, the compiler under test is built again. If the output is the same, then we have a proof that no backdoors have been inserted during the compilation.
For this scheme to work, the output of the final compilations need to be the same. And that’s exactly where reproducible builds are useful.

## DIY

### _Novice_ 👾

- Set up a simple Maven project with the [Reproducible Build Maven Plugin](https://zlika.github.io/reproducible-build-maven-plugin/) to ensure that the build is
  reproducible.
- For the previous project, experiment with different build configurations and observe how they affect the reproducibility of the build. For example, try
  building the project with
  different versions of Maven or with different sets of dependencies and see how this affects the reproducibility of the build.

### _Expert_ 💯

- Research the concept of diverse double-compilation and write a short summary explaining how it can be used to improve the reproducibility and security of
  software builds.
- Create a script file (e.g., using Bash) that can be used to automate the build process, including all necessary steps to ensure reproducibility. This may
  involve downloading and installing specific tools and dependencies, setting up build environments, and running the build itself.

# References

[^1]: [Reproducible Builds: Increasing the Integrity of Software Supply Chains](https://ieeexplore.ieee.org/document/9403390)
[^2]: [On business adoption and use of reproducible builds for open and closed source software](https://link.springer.com/article/10.1007/s11219-022-09607-z)
[^3]: [Automated Patching for Unreproducible Builds](http://oscar-lab.org/paper/icse_22_repfix.pdf)
[^5]: [An Experience Report on Producing Verifiable Builds for Large-Scale Commercial Systems](https://ieeexplore.ieee.org/document/9465650)
[^6]: [Top Five Challenges in Software Supply Chain Security: Observations From 30 Industry and Government Organizations](https://ieeexplore.ieee.org/document/9740718)
[^7]: [Reflections on Trusting Trust](https://dl.acm.org/doi/10.1145/358198.358210)
[^8]: [Countering trusting trust through diverse double-compiling](https://arxiv.org/pdf/1004.5548.pdf)