CoreCLR Intro
=============

We have few key goals with making CoreCLR sources open:

1. Address the curiosity of folks who are keen to understand the internals of managed code execution (and in turn, learn more about the guts of a virtual machine)
2. Deliver a managed runtime that can support a variety of managed code execution scenarios, especially those that are required to support ASP.NET 5.

CoreCLR is a very self-contained managed runtime that helps address these goals, while at the same time, deliver a high degree of fidelity to support managed code execution across the board. It is quicker to port to different architectures and/or platforms (especially when compared with the .NET Framework CLR) and does not have a complex install/validation process (it can be xcopied and executed). And given that it is built from the same sources as the .NET Framework CLR, folks who are interested to know learn more about low-level components (e.g. JIT, GC, TypeSystem), which are common to both, can use the sources in this repository to do so.