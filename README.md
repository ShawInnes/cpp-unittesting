# cpp-unittesting

Self-contained demo of C++ unit testing examples

# Basic Usage

## OS X / Linux

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
    conan install ..
    cmake ..
    make
    bin/demo_test

## Windows

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
    conan install ..
    cmake -G "Visual Studio 14 Win64" ..
    msbuild demo.sln

# History

- commented
- updated to support Visual Studio
- initial commit using g++ on OS X (the lib/*.a files are OS X builds)
- Added Conan 
