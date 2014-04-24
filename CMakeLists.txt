cmake_minimum_required(VERSION 2.8.11)

project(helloworld)

# Find includes in the build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Turn on automatic invocation of the MOC
set(CMAKE_AUTOMOC ON)

# Add a compiler flag
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

# Find the QtWidgets library
find_package(Qt5Widgets)

# Generate code from ui files
qt5_wrap_ui(UI_HEADERS mainwindow.ui)

# Generate rules for building source files from the resources
qt5_add_resources(QRCS resources.qrc)

# Tell CMake to create the helloworld executable
add_executable(helloworld main.cpp mainwindow.cpp ${UI_HEADERS} ${QRCS})

# Add the Qt5 Widgets for linking
target_link_libraries(helloworld Qt5::Widgets)
