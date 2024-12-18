# Software Architecture with C++
Software Architecture with C++ by Packt Publishing

<https://github.com/PacktPublishing/Software-Architecture-with-Cpp/tree/master/Chapter07/customer>

## Chapter 7: Building and Packaging

### Prerequisites

Install the following software:
- CMake 3.15
- Conan 1.62.0
- GCC 13

Assuming you're on Linux or using WSL, configure a sacpp Conan profile and remotes by running:

```bash
conan profile new sacpp || true
conan profile update settings.compiler=gcc sacpp
conan profile update settings.compiler.libcxx=libstdc++11 sacpp
conan profile update settings.compiler.version=13 sacpp
conan profile update settings.arch=x86_64 sacpp
conan profile update settings.os=Linux sacpp
```

If GCC 13 is not your default compiler, you also need to add:

```bash
conan profile update env.CXX=`which g++-13` sacpp
conan profile update env.CC=`which gcc-13` sacpp
```

### Building

To build the customer project, first cd to its source directory, and then run:
(for conan2 the conafile.txt may need to be copied to build)

```bash
mkdir build
cd build
conan install .. --build=missing -s build_type=Release -pr=sacpp
cmake .. -DCMAKE_BUILD_TYPE=Release # build type must match Conan's
cmake --build .
```

If GCC 13 is not your default compiler, you can tell CMake to use it with the `CMAKE_CXX_COMPILER` flag.
Replace the first invocation above with:

```bash
cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=`which g++-13`
```


### Testing

To run tests from each of the projects, cd into their respective build directory, and then simply run `ctest`.

### Installing

In the build directory, run `cmake --install .` to install the software into `${CMAKE_PREFIX_PATH}`. If no prefix is
given, it will install system-wide. To change this, add `-DCMAKE_INSTALL_PREFIX=/path/to/install/to` to your cmake
invocation.

### Packaging

In the build directory, run `cpack`. Simple as that. Assuming you're running on a system supporting DEB packages,
you'll get a .tar.gz file, a .zip file, and a .deb package.

### Building a Conan package

In the build directory, run `cmake --build . --target conan`.
(does not work for conan2)
