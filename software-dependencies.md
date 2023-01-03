---
layout: default
title: Software dependencies
parent: Fundamentals
nav_order: 3
description: "This chapter describes the significance of software dependencies in software development"
---

# Software Dependencies

Software dependencies are the components of a software system that are not part of the system itself, but are required for the system to function. In development environments, software dependencies are typically pulled from software repositories at build time. Software dependencies have the following characteristics:

1. They are not part of the software system itself
2. They are required for the system to function
3. They are typically pulled from software repositories at build time
4. They are typically managed by a package manager
5. They are typically versioned

Software dependencies are an important part of software development. A key aspect to understand is how they are handled by package managers. Every package manager has a different way of handling dependencies. For example, some package managers, such as Maven, will automatically pull and cache the dependencies of a package to the local filesystem, while others will download the latest version of the dependencies from the remote repository every time the application is built. Some package managers will automatically update the dependencies of a package, while others will not. Dependency resolution mechanisms and dependency updates are important aspects to consider when choosing a package manager during software development.

### _Versioning_

Dependency versioning is a mechanism that allows developers to specify the exact version of a dependency that is required to build a software project. Relying on a particular version of a dependency is important because it allows to handle the case where a dependency is updated, and the software project is not compatible with the new version of the dependency. The Semantic Versioning Specification ([SemVer](https://semver.org/)) is a popular versioning scheme that is used by many package managers to determine the impact of the code changes in the new deployed versions.

### _Dependency Trees_

Dependency trees are a way to organize the dependencies of a software project. The software project is the root of the tree, while each node in the tree represents one of its dependencies. The edges in the tree signify the relationship between the nodes, i.e., how each dependency depends on others. Package managers typically use dependency trees to visually represent the dependencies of a software project.

In a dependency tree there are three main types of nodes:

1. The root node: the software project itself
2. Direct dependencies: the dependencies that the software project directly declares through a build configuration file
3. Transitive dependencies: the dependencies of the direct dependencies, not directly declared by the software project

Transitive dependencies deserve special attention as they are not directly declared the project build configuration file, but they are used by the downstream dependencies.
For example, if the project `A` uses a dependency `B`, and `B` uses another dependency `C`, then `B` is the direct dependency of `A` and `C` is a transitive dependency that also is necessary to build `A`.

The following figure shows the dependency tree of the project [`com.github.ferstl`](https://github.com/ferstl/depgraph-maven-plugin) as resolved by the Maven package manager:

![](https://github.com/ferstl/depgraph-maven-plugin/raw/master/src/doc/by-group-id.png)

From the figure, we see that the root node is the project `com.github.ferstl` itself. The direct dependencies of the project are `commons-codec`, `org.apache.commons`, `junit`, `com.google.guava`, `org.springframework`, and `com.mysema.querydsl`, whereas the transitive dependencies are `org.hamcrest`, `com.google.code.findbugs`, `com.mysema.commons`, and `com.infradna.tool`. Moreover, direct dependency `junit` depends on `org.hamcrest`, which makes the latter a transitive dependency in `com.github.ferstl`, and so on.

### _Dependency Resolution Mechanisms_

Dependency resolution mechanisms are protocols that package managers use to determine the dependencies in the dependency tree of a software project. Different package managers use different dependency resolution mechanisms. In particular, these mechanisms facilitates the resolution of conflicts between dependency versions [^5]. This is because, in most package managers, only one version of any particular dependency can be installed at a time. In that sense, one of the primary responsibilities of the package manager is to figure out a set of dependendency versions that will satisfy every version constraint simultaneously.

> “**Dependency hell**” is a colloquial term denoting the frustration resulting from the inability to install software due to complicated dependencies [^3].

For example, the [Maven](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html) package manager relies on a comprehensive dependency resolution mechanism that determines which version of a dependency to use, based on the proximity of the dependency to the root node. On the other hand, the dependency resolution mechanism of [npm](https://medium.com/learnwithrahul/understanding-npm-dependency-resolution-84a24180901b) attempts to flatten the dependency tree as much as possible, while picking the version based on the installation order expressed in the `package.json` file.
