Qt-CMake-HelloWorld
===================

A Simple Qt5 Program Built with CMake

## Building

* MinGW Command Line - You probably have to tell CMake where to find Qt and to use MinGW instead of MSVC, so you'll probably want something along the lines of:

    C:\\...> cmake -G "MinGW Makefiles" -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake"

* Qt Creator - Depending upon your setup, you may need to tell CMake where to find Qt. This can be done by adding -DCMAKE_PREFIX_PATH="path/to/Qt5/lib/cmake" to the arguments input box in the CMake Wizard.
* Visual Studio - I usually use the CMake GUI with Visual Studio. To get everything generated properly, you'll probably need to add CMAKE_PREFIX_PATH. The details appear to depend on which versions you are using.
    * Visual Studio 2013, Qt 5.3 (OpenGL) - In addition to finding Qt, CMake will want to find the Windows SDK. For me, I set CMAKE_PREFIX_PATH to "path/to/Qt5/lib/cmake;C:\Program Files (x86)\Windows Kits\8.1\Lib\winv6.3\um\x64"
    * Everything else is untested. Submissions welcome.
