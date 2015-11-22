cmake_minimum_required(VERSION 3.3)
project(demo_tests)

set(Boost_USE_STATIC_LIBS ON)
set(Boost_USE_MULTI_THREADED ON)

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
