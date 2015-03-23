Project Priorities
==================

The current priority for the team is making [.NET Core](http://blogs.msdn.com/b/dotnet/archive/2014/12/04/introducing-net-core.aspx) work on Linux and Mac OS X.

Contribution Guidelines
=======================

Please always start your contribution with an Issue, per [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing). The recommended contribution workflow is described in those guidelines.

The team will prefer incoming PRs and issues that align with the project priority (see above). 

However, it is OK to create a broad range of issues. There may be other developers that are interested in the same topic. If a strong community viewpoint establishes itself on an issue outside of the core priority, then the team will likely engage on the issue.

Contributing to CoreCLR Repo
----------------------------

The .NET Core team maintains several guidelines for contributing to the .NET Core repos, which are provided below. Many of these are straightforward, while others may seem  subjective. A .NET Core team member will be happy to explain why a guideline is defined as it is. We can also update the wiki, as needed.

- [Contribution Bar](#contribution-bar) describes the general bar that the team uses to accept changes.
- [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing) for general .NET Contribution guidelines.
- [Garbage Collection Contributions](https://github.com/dotnet/coreclr/wiki/Garbage-Collector-Contributions) for changes that affect the GC.
- [Performance Requirements](https://github.com/dotnet/coreclr/wiki/Performance-Requirements) for changes in performance critical code or that otherwise affect performance.
- [Mscorlib Contributions](#contributing-to-mscorlib-library) for contributing to the mscorlib library
- [Contributing Ports](#contributing-ports) for contributing changes that enable .NET Core to run on other OSes and chips.

Contribution "Bar"
------------------

Changes must have a **demonstrably broad impact** of a **mainline scenario** and be **low risk** in order to be accepted. They must also satisfy the published guidelines for .NET Core.

We will be making and accepting changes to support the various .NET Core ports and that improve the product significantly for a broad set of apps. Please start with an issue before making such a change. 

We will not accept changes that have narrowly-defined benefits, due to compatibility risk. The CoreCLR codebase is used by several Microsoft products (e.g. Windows Phone, ASP.NET 5, .NET Framework 4.6) to enable execution of managed code. Changes to the open source codebase can become part of these products, but are first reviewed and tested to ensure they are correct for those products and will not inadvertently break applications. We may revert changes if they are found to be breaking.

Contributing Ports
------------------

We encourage ports of CoreCLR to other platforms. Linux and Mac OS X ports are in progress and have a lot of momentum behind them. There is also interest in a [FreeBSD port](https://github.com/dotnet/coreclr/issues/455) (and OpenBSD and NetBSD).

Ports have a weaker contribution bar, since they do not contribute to compatibility risk with existing Microsoft products on Windows. For ports, we are primarily looking for functionaly correct implementations.

Contributing to mscorlib library
--------------------------------

Most managed code changes should be made in the [CoreFX](https://github.com/dotnet/corefx) repo. We have moved and are continuing to move many mscorlib types to CoreFX. Please use the following general rule-of-thumb for choosing the right repo to make your change (start by creating an issue):

- The type or concept doesn't yet exist in .NET Core -> choose CoreFX.
- The type exists in both CoreCLR and CoreFX repo -> choose CoreFX.
- The type exists in CoreCLR only -> choose CoreCLR.
- In doubt -> choose CoreFX.

Please see [Breaking Changing](https://github.com/dotnet/corefx/wiki/Breaking-Changes) to understand our requirements on changes that could impact compatibility. Please pay the most attention to changes that affect the [Public Contract](https://github.com/dotnet/corefx/wiki/Breaking-Changes#bucket-1-public-contract). We will not accept changes that break compatibility.