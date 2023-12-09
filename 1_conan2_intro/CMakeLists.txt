cmake_minimum_required(VERSION 3.22)
project(app CXX)

find_package(spdlog CONFIG REQUIRED)

add_executable(app src/main.cpp)

target_link_libraries(app PRIVATE spdlog::spdlog)