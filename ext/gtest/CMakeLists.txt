cmake_minimum_required(VERSION 3.3)
project(gtest C CXX)
find_package(Threads REQUIRED)

include(ExternalProject)

ExternalProject_Add(
    gtest
    URL https://github.com/google/googletest/archive/release-1.7.0.tar.gz
    URL_MD5 4ff6353b2560df0afecfbda3b2763847
    CMAKE_ARGS -DCMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG:PATH=DebugLibs
               -DCMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE:PATH=ReleaseLibs
               -DCMAKE_CXX_FLAGS=${MSVC_COMPILER_DEFS}
               -Dgtest_force_shared_crt=ON
    PREFIX "${CMAKE_CURRENT_BINARY_DIR}"
    INSTALL_COMMAND ""
)

# Specify include dir
ExternalProject_Get_Property(gtest source_dir)
set(GTEST_INCLUDE_DIRS ${source_dir}/include PARENT_SCOPE)

# Specify MainTest's link libraries
ExternalProject_Get_Property(gtest binary_dir)
set(GTEST_LIBS_DIR ${binary_dir} PARENT_SCOPE)
