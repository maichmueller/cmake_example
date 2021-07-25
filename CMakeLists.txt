cmake_minimum_required(VERSION 3.4...3.18)
project(cmake_example2)

include(Conan.cmake)
run_conan()
include(${PROJECT_BINARY_DIR}/conanbuildinfo.cmake)
include(${CMAKE_BINARY_DIR}/conan_paths.cmake)

add_subdirectory(pybind11)
pybind11_add_module(cmake_example2 src/main.cpp)

# EXAMPLE_VERSION_INFO is defined by setup.py and passed into the C++ code as a
# define (VERSION_INFO) here.
target_compile_definitions(cmake_example2 PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})
