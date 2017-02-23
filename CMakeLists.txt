cmake_minimum_required(VERSION 3.3)

set(PROJECT_NAME_STR demo)
project(${PROJECT_NAME_STR} C CXX)

include(MSVC.cmake)
enable_testing()

include(${PROJECT_SOURCE_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

#-------------------
# set common include folder for module
#-------------------
set(COMMON_INCLUDES ${PROJECT_SOURCE_DIR}/include)

#-------------------
# Module Source
#-------------------
set(PROJECT_LIB_NAME ${PROJECT_NAME_STR})

include_directories(${COMMON_INCLUDES})
file(GLOB SRC_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp)
add_library(${PROJECT_LIB_NAME} ${SRC_FILES})

#-------------------
# Module Test
#-------------------

set(PROJECT_TEST_NAME ${PROJECT_NAME_STR}_test)

file(GLOB TEST_SRC_FILES ${PROJECT_SOURCE_DIR}/test/*.cpp)
add_executable(${PROJECT_TEST_NAME} ${TEST_SRC_FILES})
target_link_libraries(${PROJECT_TEST_NAME} ${PROJECT_LIB_NAME})
target_link_libraries(${PROJECT_TEST_NAME} ${CONAN_LIBS})

add_test(${PROJECT_TEST_NAME} ${PROJECT_TEST_NAME})
