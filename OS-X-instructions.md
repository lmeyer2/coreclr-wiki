These instructions will lead you through building CoreCLR and running "Hello World" on OS X.

Environment
===========

These instructions were validated on OS X Yosemite, although they probably work on earlier versions. The instructions makes use of both OS X and Windows machines, since parts of the .NET Core developer environment are not yet supported on OS X. Once those parts are supported on OS X, the Windows-specific instructions will be replaced.

CoreCLR has a dependency on CMake for the build. You can download it from [CMake downloads](http://www.cmake.org/download/).

Alternatively, you can install CMake from [Homebrew](http://brew.sh/).

    dotnet-mbp:~ richlander$ brew install cmake

Git Setup
---------

Clone the CoreCLR repository (either upstream or a fork).

    dotnet-mbp:git richlander$ git clone https://github.com/dotnet/coreclr
    Cloning into 'coreclr'...
    remote: Counting objects: 16526, done.
    remote: Compressing objects: 100% (21/21), done.
    remote: Total 16526 (delta 8), reused 0 (delta 0), pack-reused 16505
    Receiving objects: 100% (16526/16526), 26.26 MiB | 9.87 MiB/s, done.
    Resolving deltas: 100% (7679/7679), done.
    Checking connectivity... done.

This guide assumes that you've cloned the coreclr repository into ~/git/coreclr on your OS X machine and the corefx and coreclr repositories into C:\git\corefx and C:\git\coreclr on Windows. If your setup is different, you'll need to pay careful attention to the commands you run. In this guide, I'll always show you the current directory on both the OS X and Windows machine.

Build CoreCLR
=============

To Build CoreCLR, run build.sh from the root of the coreclr repo.

    dotnet-mbp:coreclr richlander$ ./build.sh

    [Lots of stuff before this]
    Repo successfully built.
	Product binaries are available at /Users/richlander/git/coreclr/binaries/Product/mac.x64.debug


Type `./build.sh -?` to see the full set of build options.

Check the build output.

    dotnet-mbp:coreclr richlander$ ls binaries/Product/mac.x64.debug/

You will see several files. The interesting ones are:

- `corerun`: The command line host. This program loads and starts the CoreCLR runtime and passes the managed program you want to run to it.
- `libcoreclr.dylib`: The CoreCLR runtime itself.

In order to keep everything tidy, let's create a new directory for the runtime and copy the runtime and corerun into it.

    dotnet-mbp:coreclr richlander$ mkdir -p ~/coreclr-demo/runtime
    dotnet-mbp:coreclr richlander$ cp binaries/Product/mac.x64.debug/corerun ~/coreclr-demo/runtime/
    dotnet-mbp:coreclr richlander$ cp binaries/Product/mac.x64.debug/libcoreclr.dylib ~/coreclr-demo/runtime/

Build mscorlib
==============

There isn't yet support for compiling managed code on OS X. The following instructions assume you are on a Windows machine with clones of both the CoreCLR and CoreFX repos and that has a correctly configured [environment](https://github.com/dotnet/coreclr/wiki/Windows-instructions#environment).

You will build mscorlib.dll out of the coreclr repository:

    C:\git\coreclr> build.cmd unixmscorlib

The output is placed in `binaries\intermediates\Unix.x64.Debug\mscorlib.dll`. You'll want to copy this to the `~/coreclr-demo/runtime` folder on your OS X machine.

Build CoreFX
============

For the rest of the framework, you need to pass some special parameters to build.cmd when building out of the CoreFX repository.

    C:\git\corefx> build.cmd /p:OS=Linux /p:SkipTests=true

It's also possible to add `/t:rebuild` to build.cmd to force it to delete the previously built assemblies.

For the purposes of Hello World, you need to copy over both bin\Unix.AnyCPU.Debug\System.Console\System.Console.dll and bin\Unix.AnyCPU.Debug\System.Diagnostics.Debug\System.Diagnostics.Debug.dll into the runtime folder on Linux. (e.g ~/coreclr-demo/runtime).

After you've done these steps, the runtime directory on Linux should look like this:

matell@linux:~$ ls ~/coreclr-demo/runtime/
corerun  libcoreclr.so  mscorlib.dll  System.Console.dll  System.Diagnostics.Debu

Compile Hello World
===================

1. Write a Hello World program. Save it.

	```
	using System;

	public class Program
	{
	    public static void Main (string[] args)
	    {
	        Console.WriteLine("Hello, OS X");
	        Console.WriteLine("Love from CoreCLR.");
	    }   
	} 
	```

2. Compile on OS X with the Mono C# compiler.
    - Install Mono from the [Mono downloads](http://www.mono-project.com/download/).
    - `dmcs -nostdlib -r:mscorlib.dll helloworld.cs`
    - Note that the [Roslyn compiler](https://github.com/dotnet/roslyn) will soon be available on Mac OS X.

3. Check the build output.
    - You should find a helloworld.exe in the appropriate location, given the compilation option you chose.

Run the program
===============

CoreCLR use a runner to run programs, unlike the way .NET programs run on Windows. This is more similar to how other development platforms work.

1. Navigate back to the build output directory on the OS X machine.
    - `cd [repo-root]/binaries/Product/mac.x64.debug`
2. Run the CoreCLR runner - corerun - to see options.
    - `./corerun`
3. Start program.
    - `./corerun -c . helloworld.exe`

    ```
    Hello, OS X
	Love from CoreCLR.
	```

Credit to Frank A. Krueger for providing the first published Mac OS X instructions @ [Building and Running .NET’s CoreCLR on OS X](http://praeclarum.org/post/110552954728/building-and-running-nets-coreclr-on-os-x).