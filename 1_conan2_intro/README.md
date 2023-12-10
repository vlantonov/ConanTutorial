# Basic App

## Instructions
1. `conan profile detect` if profile does not exist
2. `conan install .`
2. Prepare configuration 
* `cmake --preset conan-release` if using CMake>=3.23
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/1_conan2_intro/build/Release/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release` if using CMake<3.23
3. Build
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