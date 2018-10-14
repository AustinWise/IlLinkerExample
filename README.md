# IlLinker example

This is an example of how to minimize the size of a .NET Core application.
Note that it disable CrossGen, so the startup time is slower.

To compile:
```
dotnet publish -c  release -r win-x64 -o publish
```

# Results

These numbers do no include the native executables, which on
Windows X64 are about 9MB. Deleted assemblies are not included in this list.

|                        |Before linking (B)|After linking (B)|Size decrease|
|------------------------|------------------|-----------------|-------------|
|Total size of assemblies|49,773,280        |1,614,336        |96.76%       |

|Assembly Name                                        |Before linking (B)      |After linking (B)    |Size decrease|
|-----------------------------------------------------|------------------------|---------------------|-------------|
| test.dll                                            |         4,096          |      3,584          |      12.50% |
| System.Console.dll                                  |         160,848        |      34,304         |      78.67% |
| System.Memory.dll                                   |         246,376        |      6,144          |      97.51% |
| System.Resources.ResourceManager.dll                |         14,920         |      4,608          |      69.12% |
| System.Runtime.Extensions.dll                       |         394,824        |      17,920         |      95.46% |
| System.Runtime.InteropServices.dll                  |         46,184         |      7,168          |      84.48% |
| System.Runtime.dll                                  |         49,232         |      15,872         |      67.76% |
| System.Text.Encoding.Extensions.dll                 |         14,928         |      4,608          |      69.13% |
| System.Threading.Tasks.dll                          |         15,944         |      5,120          |      67.89% |
| System.Threading.dll                                |         75,880         |      12,288         |      83.81% |
| System.Private.CoreLib.dll                          |         13,028,608     |      1,502,720      |      88.47% |
