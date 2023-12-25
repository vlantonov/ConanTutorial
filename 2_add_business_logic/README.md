# Basic App

## Instructions
1. `conan profile detect` if profile does not exist
2. `conan install . -s build_type=Debug`
3. Prepare configuration
* `cmake --preset conan-debug` if using CMake>=3.23
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/2_add_business_logic/build/Debug/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug` if using CMake<3.23

## Alternative build
* `conan install . -s build_type=Debug`
* `cd build`
* `cmake .. -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./Debug/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug`
* Build can be done inside `Debug` folder using `cmake ../../ -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Debug`
