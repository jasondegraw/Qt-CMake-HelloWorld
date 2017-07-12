Qt-CMake-HelloWorld
===================

A Simple Qt5 Program Built with CMake 3.8.2

## Building

### MinGW 
From the command line, you'll probably have to tell CMake where to find Qt and to use MinGW instead of MSVC. You'll probably want something along the lines of:

```
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"MinGW Makefiles" path/to/source
```

I have also successfully used Qt Creator with MinGW. Depending upon your setup, you may need to tell CMake where to find Qt. This can be done by adding `-DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake"` to the arguments input box in the CMake Wizard.

### Visual Studio
I usually use the CMake GUI with Visual Studio, but the command line also works. To get everything generated properly, you'll need to select the right generator and probably need to point `CMAKE_PREFIX_PATH` at the CMake files in the Qt install.

CMake GUI, Visual Studio 2015, Qt 5.9.1, 64 bit: Add a path entry called `CMAKE_PREFIX_PATH` and set the value to `path/to/Qt5/lib/cmake`. Configure and select the Visual Studio 14 2015 Win64 generator. Generate and you're done.

CMake Command Line, Visual Studio 2015, Qt 5.9.1, 64 bit: Run vcvarsall, then execute CMake in your build directory:

```
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 14 2015 Win64" path/to/source
```

### Clang with Visual Studio
Newer versions of Clang and Visual Studio work pretty well together, and relatively little effort is required. After installing Clang (it may be required to add Clang to your path during the install).

CMake GUI, Visual Studio 2015, Clang 4.0.1, Qt 5.9.1, 64 bit: Add a path entry called `CMAKE_PREFIX_PATH` and set the value to `path/to/Qt5/lib/cmake`. Configure and select the Visual Studio 14 2015 Win64 generator with the toolset `LLVM-vs2014` (yes, 2014). Generate and you're done.

CMake Command Line, Visual Studio 2015, Clang 4.0.1, Qt 5.9.1, 64 bit: Run vcvarsall, then execute CMake in your build directory:

```
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 14 2015 Win64" -T"LLVM-vs2014" path/to/source
```

### Everything Else 
Everything else is untested. Submissions welcome.
