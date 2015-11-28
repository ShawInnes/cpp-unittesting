cmake_minimum_required(VERSION 3.3)
project(gmock C CXX)
find_package(Threads REQUIRED)

include(ExternalProject)

ExternalProject_Add(
    gmock
    URL https://github.com/google/googletest/archive/release-1.7.0.tar.gz
    URL_MD5 4ff6353b2560df0afecfbda3b2763847
    CMAKE_ARGS -DCMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG:PATH=DebugLibs
               -DCMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE:PATH=ReleaseLibs
               -DCMAKE_CXX_FLAGS=${MSVC_COMPILER_DEFS}
    PREFIX "${CMAKE_CURRENT_BINARY_DIR}"
    INSTALL_COMMAND ""
)

ExternalProject_Get_Property(gmock source_dir)
set(GMOCK_INCLUDE_DIRS ${source_dir}/include PARENT_SCOPE)

ExternalProject_Get_Property(gmock binary_dir)
set(GMOCK_LIBS_DIR ${binary_dir} PARENT_SCOPE)
