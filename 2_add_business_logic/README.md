# Basic App

## Instructions
1. `conan profile detect` if profile does not exist
2. `conan install .`
* If missing package error: `conan install . --build=missing`
* Using specific profile: `conan install . -pr:h=clang -pr:b=clang --build=missing`
3. Prepare configuration 
* `cmake --preset conan-release` if using CMake>=3.23 . Visual Studio Code detects it. 
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/1_conan2_intro/build/Release/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release` if using CMake<3.23
4. Build
* `cmake --build --preset conan-release` if using CMake>=3.23
* `make` in `build` folder using CMake<3.23

## Debug build
1. Set up profile as above
2. `conan install . -s "&:build_type=Debug"`
3. Prepare configuration
* `cmake --preset conan-debug` if using CMake>=3.23
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/1_conan2_intro/build/Debug/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug` if using CMake<3.23

## Alternative build
* `conan install . -s "&:build_type=Debug"`
* `cd build`
* `cmake .. -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./Debug/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug`
* Build can be done inside `Debug` folder using `cmake ../../ -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug`

## Conan profile
* `conan profile list`
* `conan profile show`
* `conan profile show --profile default`
* Create new profile: `conan profile detect --name new_profile`
* Profiles in `~/.conan2/profiles/`
* Clang profile:
```
[settings]
arch=x86_64
build_type=Release
compiler=clang
compiler.cppstd=20
compiler.libcxx=libstdc++11
compiler.version=14
os=Linux

[buildenv]
CC=/usr/bin/clang
CXX=/usr/bin/clang++

[conf]
tools.build:compiler_executables={'c':'/usr/bin/clang','cpp':'/usr/bin/clang++'}

```
* [Documentation](https://docs.conan.io/2.0/reference/config_files/profiles.html)
* [Cross building with Conan](https://docs.conan.io/2.0/tutorial/consuming_packages/cross_building_with_conan.html)