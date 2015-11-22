cmake_minimum_required(VERSION 3.3)
project(demo_tests)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(SOURCE_FILES
    demo.cpp
    demo.h
    demo_tests.cpp)

include_directories(include)
link_directories(lib)

link_libraries(gtest)
link_libraries(gtest_main)

add_executable(demo_tests ${SOURCE_FILES})
