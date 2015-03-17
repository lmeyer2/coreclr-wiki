Project Priorities
==================

The current priority for the team is making [.NET Core](http://blogs.msdn.com/b/dotnet/archive/2014/12/04/introducing-net-core.aspx) work on Linux and Mac OS X.

Contribution Guidelines
=======================

Please always start your contribution with a PR, per [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing). The recommended contribution workflow is described in those guidelines.

The team will prefer incoming PRs and issues that align with the project priority (see above). 

However, it is OK to create a broad range of issues. There may be other developers that are interested in the same topic. If a strong community viewpoint establishes itself on an issue outside of the core priority, then the team will likely engage on the issue.

Contributing to CoreCLR
------------------------

Changes must have a **demonstrably broad impact** of a **mainline scenario** and be **low risk** in order to be accepted. They must also satisfy the published guidelines for .NET Core.

The .NET Core guidelines can sometimes be subjective. A .NET Core member will be happy to explain why a guideline is defined as it is. We can also update the wiki, as needed.

- [.NET Core Contributions](https://github.com/dotnet/corefx/wiki/Contributing) for general .NET Contribution guidelines.
- [Garbage Collection Contributions](https://github.com/dotnet/coreclr/wiki/Garbage-Collector-Contributions) for changes that affect the GC.
- [Performance Requirements](https://github.com/dotnet/coreclr/wiki/Performance-Requirements) for changes in performance critical code or that otherwise affect performance.

Contributing to mscorlib
------------------------

We do not plan on accepting new features in mscorlib within the CoreCLR repo. Even bug fixes will be closely reviewed. The backwards compatibility burden we have to maintain for is quite high. CoreCLR shares a codebase with .NET Framework and is used in multiple Microsoft products.

Please make managed code changes in the [CoreFX](https://github.com/dotnet/corefx) repo, unless asked to do something different. In some cases, types exist in both the CoreCLR and CoreFX repos. In that case, too, please propose your changes on the CoreFX repo.

Please see [Breaking Changing](https://github.com/dotnet/corefx/wiki/Breaking-Changes) to understand our requirements on changes that could impact compatibility. Please pay the most attention to changes that affect the [Public Contract](https://github.com/dotnet/corefx/wiki/Breaking-Changes#bucket-1-public-contract). We will not  accept changes that break compatibility.