Microsoft Process and Systems
=============================

The Microsoft team has some internal processes that can be interesting or important to understand.

Understanding the TFS-Git Mirror
--------------------------------

CoreCLR and the .NET Framework CLR share the same source code. Since the .NET Framework code is maintained in TFS within Microsoft, it means a system is needed to flow changes out to GitHub and likewise, any changes committed on GitHub should flow back to our internal branches. The team maintains a TFS-Git bidirectional mirroring infrastructure that handles the change propogation, automaticaly and correctly.

The mirroring infrastructure uses the following hint files to mirror a given TFS folder into GitHub and back:

1. `.gitmirror` - any folder containing this file will **only** have its contained files mirrored. Subfolders are **not** mirrored.
2. `.gitmirrorall` - any folder containing this file will have all of its files **and** subfolders mirrored recursively. The subfolders do not need to have any hint files.

Thus, if you add a new folder to be included as part of the CoreCLR build, it will also need to have one of the two hint files mentioned above.

In summary, the mirror enables your contributions to make their way into both CoreCLR and the .NET Framework CLR.