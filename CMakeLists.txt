cmake_minimum_required(VERSION 3.22)
project(ExchangeGateway VERSION 1.0.0 LANGUAGES CXX)

#enforce c++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

#Define strict, omptized compiler flags for Clang
if(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    add_compile_options(
        -O3                  # Aggressive optimization for speed
        -march=native        # Vectorize instructions for your specific host CPU
        -Wall -Wextra        # Enable all standard warnings
        -Werror              # Treat warnings as errors to force clean code
        -Wpedantic           # Enforce strict ISO C++ compliance
        -Wshadow             # Warn if local variables hide outer variables
        -fno-omit-frame-pointer # Essential for accurate profiling with 'perf' later
    )

  # Use LLVM's LLD linker for significantly faster compilation turnaround times
    add_link_options(-fuse-ld=lld)
endif()

# Setup include directories
include_directories(include)

# Placeholder for your executable target (uncomment once main.cpp exists)
add_executable(exchange_gateway main.cpp)