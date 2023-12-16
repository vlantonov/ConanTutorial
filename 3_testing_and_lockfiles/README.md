# Basic App

## Instructions
1. `conan profile detect` if profile does not exist
2. `conan install . --build=missing`
3. Prepare configuration
* `cmake --preset conan-release` if using CMake>=3.23
* `cmake <path> -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=<path_to>/3_testing_and_lockfiles/build/Release/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release` if using CMake<3.23
4. `ctest --preset conan-release`
5. `ctest --preset conan-release --output-junit results.xml`

## Lockfiles for reproducible dependencies
1. One time setup: `conan lock create .`
2. Updating: `conan lock create . --lockfile="" --update`
* "" - ignores existing file
3. Automatically picked on subsequent `conan install`

## Note
* Keep version ranges simple
* `ctest` detected by `Testing` extension.
* `conan.lock` is just for example. Recreate it.
* GitHub Actions: `hello.yml`

## Alternative build
* `conan install . --build=missing`
* `cd build`
* `cmake .. -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./Release/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release`
* Build can be done inside `Release` folder using `cmake ../../ -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=./generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release`
* `make`
* `ctest`
* `cat results.xml`
