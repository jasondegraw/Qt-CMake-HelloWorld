Qt-CMake-HelloWorld
===================

A Simple Qt5 Program Built with CMake 3.8.2

## Building

### MinGW 

From the command line, you'll probably have to tell CMake where to find Qt and to use MinGW instead of MSVC. You'll probably want something along the lines of:

```cmake
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"MinGW Makefiles" path/to/source
```

I have also successfully used Qt Creator with MinGW. Depending upon your setup, you may need to tell CMake where to find Qt. This can be done by adding `-DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake"` to the arguments input box in the CMake Wizard.

### Visual Studio
I usually use the CMake GUI with Visual Studio, but the command line also works. To get everything generated properly, you'll need to select the right generator and probably need to point `CMAKE_PREFIX_PATH` at the CMake files in the Qt install.

CMake GUI, Visual Studio 2015, Qt 5.9.1, 64 bit: Add a path entry called `CMAKE_PREFIX_PATH` and set the value to `path/to/Qt5/lib/cmake`. Configure and select the Visual Studio 14 2015 Win64 generator. Generate and you're done.

CMake Command Line, Visual Studio 2015, Qt 5.9.1, 64 bit: Run vcvarsall, then execute CMake in your build directory:

```cmake
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 14 2015 Win64" path/to/source
```

### Clang with Visual Studio
Newer versions of Clang and Visual Studio work pretty well together, and relatively little effort is required. After installing Clang (it may be required to add Clang to your path during the install).

CMake GUI, Visual Studio 2015, Clang 4.0.1, Qt 5.9.1, 64 bit: Add a path entry called `CMAKE_PREFIX_PATH` and set the value to `path/to/Qt5/lib/cmake`. Configure and select the Visual Studio 14 2015 Win64 generator with the toolset `LLVM-vs2014` (yes, 2014). Generate and you're done.

CMake Command Line, Visual Studio 2015, Clang 4.0.1, Qt 5.9.1, 64 bit: Run vcvarsall, then execute CMake in your build directory:

```cmake
>cmake -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" -G"Visual Studio 14 2015 Win64" -T"LLVM-vs2014" path/to/source
```

## Conan package manager

It's possible to install Qt dependencies with using conan package manager with either conanfile.txt or conanfile.py. For instance, the example with conanfile.txt is given.

Steps for building are placed below:

* Download and install conan following the instruction:
https://docs.conan.io/en/latest/installation.html

* Add bincrafters to the conan remotes:

```cmake 
conan remote add bincrafters https://api.bintray.com/conan/bincrafters/public-conan
```
* Create the build directory:
```shell
mkdir build && cd build
```
* Run conan packages installation. Probably you'll need the --build=missing option.
```shell
conan install .. --build=missing
```

## Using the conan cmake_paths generator 

* Run cmake configuration for the project. Note, that the current conan generator is cmake_paths.
For mode details, visit https://docs.conan.io/en/latest/reference/generators/cmake_paths.html
Note, that in the examples Visual Studio generator is used, but you are free to choose it on your demand.

```shell 
cmake -DCMAKE_TOOLCHAIN_FILE=conan_paths.cmake -G"Visual Studio 16 2019" -Ax64 ..
cmake --build .
```
* Full commandline:
```shell
mkdir build
cd build
conan install .. --build=missing
cmake -DCMAKE_TOOLCHAIN_FILE=conan_paths.cmake -G"Visual Studio 16 2019" -Ax64 ..
cmake --build .
```

## Using the conan cmake_find_package generator
* uncomment the line `#cmake_find_package` in conanfile.txt
* uncomment `#include(${CMAKE_BINARY_DIR}/conan_paths.cmake)` in CMakeLists.txt
* run:
```shell
cmake -G"Visual Studio 16 2019" -Ax64 ..
cmake --build .
```

* Full commandline:
``` shell
mkdir build
cd build
conan install .. --build=missing
cmake -G"Visual Studio 16 2019" -Ax64 ..
cmake --build .
```
### Everything Else 

Everything else is untested. Submissions welcome.
