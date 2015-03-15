Building the repository
=======================

The CoreCLR repo can be built from a regular, non-admin command prompt. The build produces CoreCLR (its various native binaries), the mscorlib managed library and the accompanying tests. The repo can be built for the following platforms, using the provided instructions.

**Windows**

- X64

[Windows Instructions](https://github.com/dotnet/coreclr/wiki/Windows-Instructions)


**Linux**

- X64

[Linux Instructions](https://github.com/dotnet/coreclr/wiki/Linux-Instructions)

**Mac OS X**

- X64

[Instructions](https://github.com/dotnet/coreclr/wiki/MacOSX-Instructions)

The CoreCLR build and test suite is a work in progress. Microsoft and the community are improving Linux and Mac OS X support on a daily basis are and adding more tests for all platforms. See [CoreCLR Issues](https://github.com/dotnet/coreclr/issues) to find out about specific work items or report issues.

Contribution Overview
=====================

Please read the [Contribution Guidelines](https://github.com/dotnet/coreclr/wiki/Contribution-guidelines) and [Contribution Workflow](https://github.com/dotnet/coreclr/wiki/Contribution-workflow) before making your first contribution.

The CoreCLR codebase is a very important asset for Microsoft. CoreCLR is used by several Microsoft products (e.g. Windows Phone, ASP.NET 5, to name a few) to enable execution of managed code. It is also built from the same code as the .NET Framework CLR, such that a change to CoreCLR often becomes part of the .NET Framework CLR, too. Contributions to this repo can be tremendously valuable and positively impact millions of Microsoft customers. They can also inadvertly break apps. Contributions will be reviewed very closely to ensure that they are safe.

