# IlLinker example

This is an example of how to minimize the size of a .NET Core application.
Note that it disable CrossGen, so the startup time is slower.

To compile:
```
dotnet publish -c Release -r win-x64
```

# Results for .NET Core 3.1

In the .NET Core SDK 3.1 this is acomplished by poking an internal MSBuild property.
Ideally there would be a documented way to change these properties.

These numbers do no include the native executables, which on
Windows X64 are about 16MB. Deleted assemblies are not included in this list.
Some of these native files are related to debugging and couple be excluded to
reduce the size by a few megabytes.

|                        |Before linking (B)|After linking (B)|Size decrease|
|------------------------|------------------|-----------------|-------------|
|Total size of assemblies|52,255,016        |1,770,496        |96.61%       |

|Assembly Name                                        |Before linking (B)      |After linking (B)    |Size decrease|
|-----------------------------------------------------|------------------------|---------------------|-------------|
| test.dll                                            |         4,096          |      3,584          |      12.50% |
| System.Console.dll                                  |         152,440        |      32,768         |      78.50% |
| System.Runtime.InteropServices.dll                  |         53,112         |      8,192          |      84.58% |
| System.Private.CoreLib.dll                          |         9,556,040      |      1,725,952      |      81.94% |

# Results for .NET Core 2.1

See the `netcore21` branch.
