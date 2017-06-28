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
    pip install conan

### Workaround for Windows Visual Studio

Sometimes conan doesn't correctly identify the local compiler.  The following settings go in `%homepath%\.conan\conan.conf`

```
[settings_defaults]
arch=x86_64
os=Windows
compiler=Visual Studio
compiler.version=15
compiler.runtime=MD
build_type=Release
```

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

## Windows

    git clone https://github.com/shawinnes/cpp-unittesting
    cd cpp-unittesting
    mkdir build
    cd build
	conan install .. -s compiler="Visual Studio" -s compiler.version=15 -s compiler.runtime=MT --build missing
    cmake -G "Visual Studio 15 Win64" ..
    msbuild demo.sln /p:Configuration=Release    

> for some reason Debug is broken with the introduction of googletest from conan
> work required.

# History

- commented
- updated to support Visual Studio
- initial commit using g++ on OS X (the lib/*.a files are OS X builds)
- Added Conan
