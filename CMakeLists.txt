cmake_minimum_required(VERSION 3.20)
project(tinyLog LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(tinyLog STATIC)

# Source and header files
target_sources(tinyLog
    PRIVATE
        src/Log.cpp
        src/ccprintf.h
    PUBLIC
        include/tinyLog/Log.h
        include/tinyLog/Asserts.h
)

# Include paths:
#   - include/ is visible to users (PUBLIC)
#   - src/ is only visible internally (PRIVATE)
target_include_directories(tinyLog
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_compile_features(tinyLog PUBLIC cxx_std_20)