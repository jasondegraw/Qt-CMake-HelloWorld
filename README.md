Qt-CMake-HelloWorld
===================

A Simple Qt5 Program Built with CMake

## Building

### MinGW 
From the command line, you'll probably have to tell CMake where to find Qt and to use MinGW instead of MSVC. You'll probably want something along the lines of:

```
> cmake -G "MinGW Makefiles" -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" path/to/source
```

I have also successfully used Qt Creator with MinGW. Depending upon your setup, you may need to tell CMake where to find Qt. This can be done by adding -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" to the arguments input box in the CMake Wizard.

### Visual Studio
I usually use the CMake GUI with Visual Studio, but the command line also works. To get everything generated properly, you'll need to select the right generator and probably need to add CMAKE_PREFIX_PATH. The details appear to depend on which versions you are using.

CMake GUI, Visual Studio 2013, Qt 5.3 (OpenGL), 64 bit - Select the Visual Studio 12 Win64 generator. In addition to finding Qt, CMake will want to find the Windows SDK. For me, I set CMAKE_PREFIX_PATH to "path/to/Qt5/lib/cmake;C:\Program Files (x86)\Windows Kits\8.1\Lib\winv6.3\um\x64"

CMake Command Line, Visual Studio 2013, Qt 5.3 (OpenGL), 64 bit - If executed after vcvarsall, then CMake will only need to know where Qt is:

```
C:\...\Qt-CMake-HelloWorld\build-vs2013-cli>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 12 Win64" ..
```

### Clang with Visual Studio
I've had some success building with Clang on Windows, at least with recent versions of Visual Studio. For Clang 4.0.1 and Qt 5.9.1 (5.8 does not work, 5.9.0 might), after executing vcvarsall:

```
C:\...\Qt-CMake-HelloWorld\build-clang>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 14 2015 Win64" -T"LLVM-vs2014" ..
```

The "vs2014" bit is a little confusing, but apparently correct.

### Everything Else 
Everything else is untested. Submissions welcome.
