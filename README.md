# IlLinker example

This is an example of how to minimize the size of a .NET Core application.
Note that it disable CrossGen, so the startup time is slower.

To compile:
```
dotnet publish -c  release -r win-x64 -o publish
```

# Results for .NET Core 2.1

These numbers do no include the native executables, which on
Windows X64 are about 8MB. Deleted assemblies are not included in this list.

|                        |Before linking (B)|After linking (B)|Size decrease|
|------------------------|------------------|-----------------|-------------|
|Total size of assemblies|49,755,624        |1,615,872        |96.75%       |

|Assembly Name                                        |Before linking (B)      |After linking (B)    |Size decrease|
|-----------------------------------------------------|------------------------|---------------------|-------------|
| test.dll                                            |         4,096          |      3,584          |      12.50% |
| System.Console.dll                                  |         160,632        |      34,304         |      78.64% |
| System.Memory.dll                                   |         246,136        |      6,144          |      97.50% |
| System.Resources.ResourceManager.dll                |         14,928         |      4,608          |      69.13% |
| System.Runtime.Extensions.dll                       |         394,616        |      17,920         |      95.46% |
| System.Runtime.InteropServices.dll                  |         46,456         |      7,168          |      84.57% |
| System.Runtime.dll                                  |         49,016         |      15,872         |      67.62% |
| System.Text.Encoding.Extensions.dll                 |         14,712         |      4,608          |      68.68% |
| System.Threading.Tasks.dll                          |         15,952         |      5,120          |      67.90% |
| System.Threading.dll                                |         75,640         |      12,288         |      83.75% |
| System.Private.CoreLib.dll                          |         13,026,168     |      1,504,256      |      88.45% |