Project Priorities
==================

The current priority for the team is making [.NET Core](http://blogs.msdn.com/b/dotnet/archive/2014/12/04/introducing-net-core.aspx) work on Linux and Mac OS X.

Contribution Guidelines
=======================

Please always start your contribution with an Issue, per [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing). The recommended contribution workflow is described in those guidelines.

The team will prefer incoming PRs and issues that align with the project priority (see above). 

However, it is OK to create a broad range of issues. There may be other developers that are interested in the same topic. If a strong community viewpoint establishes itself on an issue outside of the core priority, then the team will likely engage on the issue.

Contribution "Bar"
------------------

Changes must have a **demonstrably broad impact** of a **mainline scenario** and be **low risk** in order to be accepted. They must also satisfy the published guidelines for .NET Core.

Contributing to CoreCLR Repo
----------------------------

The .NET Core team maintains several guidelines for contributing to the .NET Core repos, which are provided below. Many of these are straightforward, while others may seem  subjective. A .NET Core member will be happy to explain why a guideline is defined as it is. We can also update the wiki, as needed.

- [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing) for general .NET Contribution guidelines.
- [Garbage Collection Contributions](https://github.com/dotnet/coreclr/wiki/Garbage-Collector-Contributions) for changes that affect the GC.
- [Performance Requirements](https://github.com/dotnet/coreclr/wiki/Performance-Requirements) for changes in performance critical code or that otherwise affect performance.

The CoreCLR codebase is used by several Microsoft products (e.g. Windows Phone, ASP.NET 5, .NET Framework 4.6) to enable execution of managed code. Changes to the open source codebase can become part of these products, but are first reviewed and tested to ensure they are correct for those products and will not inadvertently break applications.

Contributing to mscorlib library
--------------------------------

We do not plan on accepting new features in mscorlib within the CoreCLR repo. Even bug fixes will be closely reviewed. The backwards compatibility burden we have to maintain for is quite high. CoreCLR shares a codebase with .NET Framework and is used in multiple Microsoft products.

Please make managed code changes in the [CoreFX](https://github.com/dotnet/corefx) repo, unless asked to do something different. In some cases, types exist in both the CoreCLR and CoreFX repos. In that case, too, please propose your changes on the CoreFX repo.

Please see [Breaking Changing](https://github.com/dotnet/corefx/wiki/Breaking-Changes) to understand our requirements on changes that could impact compatibility. Please pay the most attention to changes that affect the [Public Contract](https://github.com/dotnet/corefx/wiki/Breaking-Changes#bucket-1-public-contract). We will not  accept changes that break compatibility.