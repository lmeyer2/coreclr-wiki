Contribution Workflow
=====================

We use and recommend the following workflow:

1. Create an [issue](https://github.com/dotnet/coreclr/issues) for your work. 
	- Get agreement from the team and the community that your proposed change is a good one and then clearly state that you are going to take on implementing it. 
	- The issue filer and the implementer don't have to be the same person.
2. Create a personal fork of CoreCLR repository on GitHub.
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
8. Create a pull request (PR) against the **dotnet/coreclr** repository's **master** branch

Note: It is OK for your PR to include a large number of commits. Once your change is accepted, you will be asked to squash your commits into one or some appropriately small number of commits before your PR is merged.

PRs will go through the usual GitHub review process. The [dotnet continuous integration](http://dotnet-ci.cloudapp.net/) (CI) system will automatically perform the required builds and run tests (including the ones you are expected to run) for PRs. If the builds are clean, tests are passing and **at-least 2 developers** (could be more, depending on the context and nature of the change) from the .NET Runtime team have signed off on the change, the PR will be approved and merged.

If the CI build fails for any reason, the PR issue will be updated with a link that can be used to determine the cause of the failure.

There is currently minimal test coverage for Linux and Mac OS X builds that can be used by the dotnet CI. We are working to improve that so that more issues can be caught in CI, as is the case with Windows.