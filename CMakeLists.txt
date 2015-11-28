cmake_minimum_required(VERSION 3.3)

set(PROJECT_NAME_STR demo)
project(${PROJECT_NAME_STR} C CXX)

#-------------------
# set common include folder for module
#-------------------
set(COMMON_INCLUDES ${PROJECT_SOURCE_DIR}/include ${PROJECT_SOURCE_DIR}/gtest-1.7.0/include)

#-------------------
# Module Source
#-------------------
set(PROJECT_LIB_NAME ${PROJECT_NAME_STR})

include_directories(${COMMON_INCLUDES})
file(GLOB SRC_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp)
add_library(${PROJECT_LIB_NAME} ${SRC_FILES})

#-------------------
# Goole Test
#-------------------
add_library(gtest  "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0/src/gtest-all.cc")
set_property(TARGET gtest PROPERTY INCLUDE_DIRECTORIES
    "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0"
    "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0/include")

add_library(gtestmain  "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0/src/gtest_main.cc")
set_property(TARGET gtestmain PROPERTY INCLUDE_DIRECTORIES
    "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0"
    "${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0/include")

#-------------------
# Module Test
#-------------------
enable_testing()

set(PROJECT_TEST_NAME ${PROJECT_NAME_STR}_test)

file(GLOB TEST_SRC_FILES ${PROJECT_SOURCE_DIR}/test/*.cpp)
add_executable(${PROJECT_TEST_NAME} ${TEST_SRC_FILES})
target_link_libraries(${PROJECT_TEST_NAME} ${PROJECT_LIB_NAME})
target_link_libraries(${PROJECT_TEST_NAME} gtest)
target_link_libraries(${PROJECT_TEST_NAME} gtestmain)

add_test(${PROJECT_TEST_NAME} ${PROJECT_TEST_NAME})

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
