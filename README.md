# cpp-unittesting

Self-contained demo of C++ unit testing examples

# Basic Usage

## OS X / Linux

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
    cmake ..
    make
    ctest -V

## Windows

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
    cmake ..
    msbuild demo.sln
    ctest -V

# History

- commented
- updated to support Visual Studio
- initial commit using g++ on OS X (the lib/*.a files are OS X builds)
