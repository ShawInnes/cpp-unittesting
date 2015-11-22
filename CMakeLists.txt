cmake_minimum_required(VERSION 3.3)
project(demo_tests)

include_directories(include)
link_directories(lib)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(SOURCE_FILES
    demo.cpp
    demo.h
    demo_tests.cpp)

add_executable(demo_tests ${SOURCE_FILES})

target_link_libraries(demo_tests
    debug gtestd optimized gtest
    debug gtest_maind optimized gtest_main)

if(MSVC)
  foreach(flag_var CMAKE_CXX_FLAGS CMAKE_CXX_FLAGS_DEBUG CMAKE_CXX_FLAGS_RELEASE CMAKE_CXX_FLAGS_MINSIZEREL CMAKE_CXX_FLAGS_RELWITHDEBINFO)
      if(${flag_var} MATCHES "/MD")
          string(REGEX REPLACE "/MD" "/MT" ${flag_var} "${${flag_var}}")
      endif(${flag_var} MATCHES "/MD")
      if(${flag_var} MATCHES "/MDd")
          string(REGEX REPLACE "/MDd" "/MTd" ${flag_var} "${${flag_var}}")
      endif(${flag_var} MATCHES "/MDd")
  endforeach(flag_var)
endif(MSVC)
