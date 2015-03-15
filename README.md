CoreCLR Wiki Repo
=================

GitHub wikis are repos, but do not enable the regular PR workflow. This repo is a remote for the real wiki repo to enable that workflow. The setup is a bit odd, but it mostly works.

Here's the recommended way to participate.

**Repo setup**

- Fork https://github.com/dotnet/coreclr-wiki.
- Clone that forked repo locally. Your fork will (naturally) be origin.
- Add coreclr-wiki as a remote, called 'scratch'.
	- `git remote add scratch https://github.com/dotnet/coreclr-wiki'
- Add coreclr.wiki, the real wiki, as a remote called 'upstream'.
	- `git remote add upstream https://github.com/dotnet/coreclr.wiki`

**Alternative Repo setup if you have write access to coreclr-wiki**

- Clone coreclr-wiki repo locally. It will (naturally) be origin.
	- `git clone https://github.com/dotnet/coreclr-wiki`
- Add coreclr.wiki as a remote called 'upstream'.
	- `git remote add upstream https://github.com/dotnet/coreclr.wiki`

**Staying current**

- Pull from upstream to get the latest changes.
	- `git pull upstream master`
- Additionally, you can keep your remote fork on GitHub current.
	- `git push`

**Making changes**

- Ensure that your repo state is current.
- Make your changes in a branch
	- `git checkout -b [myname-updates]`
- Create a PR on https://github.com/dotnet/coreclr-wiki on master.
- As a side-effect of this setup, you may end up including changes from coreclr.wiki to coreclr-wiki that are not yours, in your PR. That's not avoidable with this setup.

**Looking at a PR on coreclr-wiki, via git**

- Fetch the repo state from the originating repo for the PR.
	- `git fetch [repo-url]`
	- `git checkout [branch-name]`

**Keeping coreclr.wiki and coreclr-wiki current**

Someone with write access to these two wikis needs to keep them both current. These instructions assume the alternative repo setup described above. If .NET Core team members have made changes via the GitHub web UI on coreclr.wiki, there will probably be a need for merges.

- Pull coreclr.wiki updates.
	- `git pull upstream master`
	- Merge if needed.
- Pull coreclr-wiki updates.
	- `git pull`
	- Merge if needed.
- Push changes, to coreclr.wiki and coreclr-wiki.
	- `git push upstream`
	- `git push`
