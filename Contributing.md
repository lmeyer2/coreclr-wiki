Project Priorities
==================

The current priority for the team is making [.NET Core](http://blogs.msdn.com/b/dotnet/archive/2014/12/04/introducing-net-core.aspx) work on Linux and Mac OS X. 

For proposed product changes, the team has a strong bias to **demonstrable impact** and are relatively **low risk** to implement. The team is most likely to engage on issues and resultant PRs that meet this characteristic

However, we encourage creating a broad range of issues. There are lots of folks that may respond, particularly if there are others that are interested in the same topic. If a strong community viewpoint establishes itself on an issue outside of the core priority, then the team should engage on the issue.

Contribution Guidelines
=======================

For general .NET Contribution guidelines, please refer to [CoreFX Contributions](https://github.com/dotnet/corefx/wiki/Contributing).

- [Garbage Collection Contributions](https://github.com/dotnet/coreclr/wiki/Garbage-Collector-Contributions)
- [Performance Requirements](https://github.com/dotnet/coreclr/wiki/Performance-Requirements)

Contribution Workflow
=====================

We use and recommend the following workflow:

1. Create an [issue](https://github.com/dotnet/coreclr/issues) for your work. 
	- Get agreement from the team and the community that your proposed change is a good one.
	- Clearly state that you are going to take on implementing it, if that's the case. The issue filer and the implementer don't have to be the same person.
2. Create a personal fork of CoreCLR repository on GitHub (if you don't already have one).
3. Create a branch off of master (`git checkout -b mybranch`). 
	- Name the branch so that it clearly communicates your intentions, such as issue-123 or githubhandle-issue. 
	- Branches are useful since they isolate your changes from incoming changes from upstream. They also enable you to create multiple PRs from the same fork.
4. Make your changes.
	- Please format your commits using this [commit messages style](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).
5. Build CoreCLR.
	- Make sure that the builds are clean.
	- Make sure that the tests are are passing.
6. Add a new test corresponding to your change, if applicable. Validate that it passes.
7. Commit your changes and push your changes to your fork on GitHub
8. Create a pull request (PR) against the **dotnet/coreclr** repository's **master** branch.
	- If you are working on a project in a CoreCLR feature branch, then please target that branch with your PR.

Note: It is OK for your PR to include a large number of commits. Once your change is accepted, you will be asked to squash your commits into one or some appropriately small number of commits before your PR is merged.

PR - CI Process
===============

The [dotnet continuous integration](http://dotnet-ci.cloudapp.net/) (CI) system will automatically perform the required builds and run tests (including the ones you are expected to run) for PRs. Builds and test runs must be clean.

If the CI build fails for any reason, the PR issue will be updated with a link that can be used to determine the cause of the failure.

There is currently minimal test coverage for Linux and Mac OS X builds that can be used by the dotnet CI. We are working to improve that so that more issues can be caught in CI, as is the case with Windows.

PR Review
=========

Team and community members will provide feedback on your change. Community feedback is highly valued. You will often see the absense of team feedback if the community has already provided good review feedback. 

Based on the size and impact of the change, and your history with the CoreCLR community, 1-2 core members will review every PR prior to merge.

You may be asked to meet the published requirements for [performance](https://github.com/dotnet/coreclr/wiki/Performance) and [GC contributions](https://github.com/dotnet/coreclr/wiki/Garbage-Collector-Contributions).

CoreCLR is used by several Microsoft products (e.g. Windows Phone, ASP.NET 5) to enable execution of managed code. It is also shares a codebase with the .NET Framework CLR, such that a change to CoreCLR can become part of the .NET Framework CLR. Contributions to this repo can be tremendously valuable and positively impact many Microsoft customers. They can also inadvertly break apps. Contributions will be reviewed very closely to ensure that they are safe.