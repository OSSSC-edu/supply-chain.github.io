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


Reproducible builds in software development refer to the practice of creating software builds that can be independently reproduced and verified by other parties
This is important because it allows developers to ensure the integrity and security of their software, and it allows users to verify that the software they are using has not been tampered with.

There are several benefits to reproducible builds in software development.
One benefit is that it helps to ensure the integrity of the software.
When a build is reproducible, it means that anyone who has access to the source code and build instructions can recreate the build and verify that it is the same as the original.
This can help to prevent tampering or the inclusion of malicious code in the software.

Another benefit of reproducible builds is that it allows developers to more easily identify and fix bugs in their software.
When a build is reproducible, it means that developers can reproduce the build on their own systems in order to debug and troubleshoot any issues that may arise.
This can save time and effort compared to trying to recreate a build from scratch or relying on users to report issues with the software.

Reproducible builds can also help to improve the security of software.
When a build is reproducible, it means that users can verify that the software they are using has not been tampered with or modified in any way.
This can be especially important for software that is used in critical infrastructure or other sensitive applications.

There are several factors that can affect the reproducibility of a build.
One factor is the use of external dependencies, such as libraries or other software that is included in the build.
If these dependencies are not properly managed and controlled, it can be difficult to reproduce the build.
Another factor is the build environment, including the operating system, compilers, and other tools used to create the build.
If the build environment is not consistent, it can be difficult to reproduce the build.

In order to create reproducible builds, developers can follow a number of best practices.
These can include using version control systems to manage the source code and build instructions, using consistent build environments, and properly managing external dependencies.
It can also be helpful to use automated tools and processes to ensure the reproducibility of builds.

Overall, reproducible builds are an important aspect of software development that can help to ensure the integrity and security of software, as well as improve the reliability and maintainability of the software over time.
By following best practices for reproducible builds, developers can create software that is more trustworthy and can be more easily verified and reproduced by other parties.


# Example: The GNU/Linux OS

One example of a system that employs reproducible builds is the GNU/Linux operating system.
The GNU/Linux operating system is a free and open-source operating system that is used on a wide range of devices, including servers, desktop computers, and embedded systems.

The GNU/Linux operating system is built using a process called "cross-compilation," which allows developers to build the operating system on one platform (such as a desktop computer) and then run it on another platform (such as an embedded system).
This process relies on reproducible builds in order to ensure the integrity and security of the operating system.

To create reproducible builds of the GNU/Linux operating system, developers follow a set of best practices that are outlined in the GNU Reproducible Builds project.
These practices include using version control systems to manage the source code and build instructions, using consistent build environments, and properly managing external dependencies.

In addition, the GNU/Linux operating system uses a variety of automated tools and processes to ensure the reproducibility of builds.
For example, the operating system includes a tool called "diffoscope" that can compare two builds and identify any differences between them.
This tool can be used to verify that two builds are identical and thus reproducible.

Overall, the GNU/Linux operating system is an example of a system that relies on reproducible builds in order to ensure the integrity and security of the software.
By following best practices for reproducible builds and using automated tools and processes, the developers of the GNU/Linux operating system are able to create software that is more trustworthy and can be more easily verified and reproduced by other parties.


# Tools

There are several tools that can be used to create reproducible builds, depending on the specific needs and requirements of the software project. 
Some common tools that are used for this purpose include:

Version control systems: Version control systems, such as Git or Subversion, are used to manage the source code and build instructions for a software project. 
These systems allow developers to track changes to the codebase, revert changes if necessary, and collaborate with other developers. 
By using a version control system, developers can ensure that the source code and build instructions are well-organized and easily accessible, which can help to make builds more reproducible.

Build automation tools: Build automation tools, such as Make or Gradle, are used to automate the build process for software projects. 
These tools allow developers to specify the steps required to build the software and then execute those steps automatically.
By using a build automation tool, developers can more easily reproduce builds and ensure that the build process is consistent and reliable.

Package managers: Package managers, such as npm or pip, are used to manage external dependencies for a software project.
These tools allow developers to easily install and update the libraries and other software dependencies that are needed to build the software.
By using a package manager, developers can more easily manage external dependencies and ensure that builds are reproducible.

Continuous integration tools: Continuous integration tools, such as Jenkins or Travis CI, are used to automate the build and test process for software projects.
These tools allow developers to automatically build and test the software whenever changes are made to the codebase.
By using a continuous integration tool, developers can more easily ensure that builds are reproducible and that the software is working as expected.

Overall, there are many tools that can be used to create reproducible builds, and the specific tools that are used will depend on the needs and requirements of the software project. 
By using the right tools and following best practices for reproducible builds, developers can create software that is more trustworthy and can be more easily verified and reproduced by other parties.


This configuration file specifies the tools and settings that will be used to create a reproducible build of the software.
The file specifies the version control system, build automation tool, package manager, and continuous integration tool that will be used, as well as the build environment and the dependencies for the build. 
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

# References

[^1]: [Reproducible Builds: Increasing the Integrity of Software Supply Chains](https://ieeexplore.ieee.org/document/9403390)
[^2]: [On business adoption and use of reproducible builds for open and closed source software](https://link.springer.com/article/10.1007/s11219-022-09607-z)
[^3]: [Automated Patching for Unreproducible Builds](http://oscar-lab.org/paper/icse_22_repfix.pdf)
[^4]: [Reproducible Build Maven Plugin](https://zlika.github.io/reproducible-build-maven-plugin/)