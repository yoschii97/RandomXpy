cmake_minimum_required(VERSION 2.8.12)
project(RandomXpy)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++ -v")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -stdlib=libc++ -lc++abi")

add_subdirectory(external/pybind11)
add_subdirectory(external/RandomX)
include_directories(${RANDOMX_INCLUDE})
pybind11_add_module(RandomXpy src/main.cpp src/rx-slow-hash.c)
target_link_libraries(RandomXpy PRIVATE randomx)


