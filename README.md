# cpp-unittesting

Self-contained demo of C++ unit testing examples

# Setup

## OS X

    brew update
    brew install cmake
    brew install conan

## Windows

    choco install cmake
    choco install python
    pip install --upgrade conan

# Basic Usage

## OS X / Linux

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
    conan install .. --build missing
    cmake ..
    make
    bin/demo_test

## Windows Release

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build-rel
    cd build-rel
    conan install .. -s compiler="Visual Studio" -s compiler.version=15 -s compiler.runtime=MT --build missing
    cmake -G "Visual Studio 15 Win64" ..
    msbuild demo.sln /p:Configuration=Release

## Windows Release

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build-rel
    cd build-rel
    conan install .. -s compiler="Visual Studio" -s compiler.version=15 -s compiler.runtime=MTd --build missing
    cmake -G "Visual Studio 15 Win64" ..
    msbuild demo.sln /p:Configuration=Debug

# History

- commented
- updated to support Visual Studio
- initial commit using g++ on OS X (the lib/*.a files are OS X builds)
- Added Conan
