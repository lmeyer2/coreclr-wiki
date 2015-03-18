Intro to CoreCLR
================

CoreCLR is a self-contained .NET runtime that implements [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/dotnet-standards.md). It is relatively straightforward to port to various architectures and/or platforms. It support a variety of installation options, having no specific deployment requirements itself.

The [Book of the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/index.md) is a great source of information and insight to learn more about CoreCLR. 

Building the repository
=======================

The CoreCLR repo can be built from a regular, non-admin command prompt. The build produces CoreCLR (multiple native binaries), the mscorlib managed library and the accompanying tests. The repo can be built for the following platforms, using the provided instructions.

| Chip  | Windows | Linux | OS X |
| :---- | :-----: | :---: | :--: |
| x64   | &#x25CF;| &#x25D2;| &#x25D2; |		  
| x86   | &#x25EF;| &#x25EF;| &#x25EF;|
| ARM32 | &#x25EF; | &#x25EF;| &#x25EF; |
|       | [Instructions][Windows-instructions] | [Instructions][Linux-instructions] | [Instructions][OSX-instructions] |  

[Windows-instructions]: https://github.com/dotnet/coreclr/wiki/Windows-Instructions
[Linux-instructions]: https://github.com/dotnet/coreclr/wiki/Linux-Instructions
[OSX-instructions]: https://github.com/dotnet/coreclr/wiki/Mac-OS-X-instructions

The CoreCLR build and test suite is a work in progress. The .NET Core team and the community are improving Linux and Mac OS X support on a daily basis are and adding more tests for all platforms. See [CoreCLR Issues](https://github.com/dotnet/coreclr/issues) to find out about specific work items or report issues.

Support for x86 and ARM32 will come over time. The priority is to bring up x64. 

Contributing
============

Please read [Contributing](https://github.com/dotnet/coreclr/wiki/Contributing) to .NET Core before making your first contribution.

Understanding the TFS-Git Mirror
================================

The Microsoft team maintains a Microsoft-internal TFS server of CoreCLR. An automated system is used to flow changes in/out of GitHub. The mirroring infrastructure uses the following hint files to mirror a given TFS folder into GitHub and back:

1. `.gitmirror` - any folder containing this file will **only** have its contained files mirrored. Subfolders are **not** mirrored.
2. `.gitmirrorall` - any folder containing this file will have all of its files **and** subfolders mirrored recursively. The subfolders do not need to have any hint files.

Thus, if you add a new folder to be included as part of the CoreCLR build, it will also need to have one of the two hint files mentioned above.