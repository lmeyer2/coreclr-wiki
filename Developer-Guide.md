Intro to CoreCLR
================

CoreCLR is a self-contained .NET runtime that implements [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/dotnet-standards.md). It is relatively straightforward to port to various architectures and/or platforms. It support a variety of installation options, having no specific deployment requirements itself.

Building the repository
=======================

The CoreCLR repo can be built from a regular, non-admin command prompt. The build produces CoreCLR (multiple native binaries), the mscorlib managed library and the accompanying tests. The repo can be built for the following platforms, using the provided instructions.

| Chip  | Windows | Linux | OS X |
| :---- | :-----: | :---: | :--: |
| x64   | &#x25C9;| &#x25D2;| &#x25D2; |		  
| x86   | &#x25CB;| &#x25CB;| &#x25CB;|
| ARM32 | &#x25CB; | &#x25CB;| &#x25CB; |
|       | [Instructions][Windows-instructions] | [Instructions][Linux-instructions] | [Instructions][OSX-instructions] |  

[Windows-instructions]: https://github.com/dotnet/coreclr/wiki/Windows-Instructions
[Linux-instructions]: https://github.com/dotnet/coreclr/wiki/Linux-Instructions
[OSX-instructions]: https://github.com/dotnet/coreclr/wiki/Mac-OS-X-instructions

The CoreCLR build and test suite is a work in progress. The .NET Core team and the community are improving Linux and Mac OS X support on a daily basis are and adding more tests for all platforms. See [CoreCLR Issues](https://github.com/dotnet/coreclr/issues) to find out about specific work items or report issues.

Support for x86 and ARM32 will come over time. The priority is to bring up x64. 

Contributing
============

Please read [Contributing](https://github.com/dotnet/coreclr/wiki/Contribution-guidelines) to .NET Core before making your first contribution.

In some cases, types exist in both the CoreCLR and CoreFX repos, due to backwards compatibility (e.g. Windows Phone, .NET Framework). Please make managed code changes in the CoreFX repo, unless asked to do something different.

Validating your Changes
=======================

It may be valuable to use CoreFX tests to validate your changes to CoreCLR.

In order to do this you need to create a file called `localpublish.props` under the `<repo root>\packages` folder.
The contents of the file should look like this (make sure to update the version to the current version of the CoreCLR package used by CoreFx):

	<Project ToolsVersion="12.0" DefaultTargets="Build" 
		     xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <ItemGroup>
    	<LocalPackages Include="$(PackagesBinDir)">
          <PackageName>Microsoft.DotNet.CoreCLR</PackageName>
          <PackageVersion>1.0.2-prerelease</PackageVersion>
          <InstallLocation><corefx repo root>\packages</InstallLocation>
        </LocalPackages>
      </ItemGroup>
    </Project>

Once this file is there, subsequent builds of the CoreCLR repo will install the CoreCLR package into the location specified by `InstallLocation`.

To run tests, follow the procedure for running tests in CoreFX.

Understanding the TFS-Git Mirror
================================

The Microsoft team maintains a Microsoft-internal TFS server of CoreCLR. An automated system is used to flow changes in/out of GitHub. The mirroring infrastructure uses the following hint files to mirror a given TFS folder into GitHub and back:

1. `.gitmirror` - any folder containing this file will **only** have its contained files mirrored. Subfolders are **not** mirrored.
2. `.gitmirrorall` - any folder containing this file will have all of its files **and** subfolders mirrored recursively. The subfolders do not need to have any hint files.

Thus, if you add a new folder to be included as part of the CoreCLR build, it will also need to have one of the two hint files mentioned above.