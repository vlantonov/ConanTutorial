# Basic App

## Instructions
1. `conan profile detect` if profile does not exist
2. `conan install .`
2. Prepare configuration 
* `cmake --preset conan-release` if using CMake>=3.23
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/1_conan2_intro/build/Release/generators/conan_toolchain.cmake -DCMAKE_POLICY_DEFAULT_CMP0091=NEW -DCMAKE_BUILD_TYPE=Release` if using CMake<3.23
3. Build
* `cmake --build --preset conan-release` if using CMake>=3.23
* `make` in `build` folder using CMake<3.23