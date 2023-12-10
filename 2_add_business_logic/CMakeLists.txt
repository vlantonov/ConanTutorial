cmake_minimum_required(VERSION 3.22)
project(app CXX)

find_package(spdlog CONFIG REQUIRED)
# for our particles
find_package(glfw3 CONFIG REQUIRED)
find_package(glad CONFIG REQUIRED)
find_package(linmath.h CONFIG REQUIRED)
find_package(tinycthread CONFIG REQUIRED)

add_executable(app src/main.cpp src/particles.hpp)

target_compile_features(app PRIVATE c_std_11)
target_link_libraries(app PRIVATE spdlog::spdlog glfw glad::glad
                                  linmath.h::linmath.h tinycthread::tinycthread)