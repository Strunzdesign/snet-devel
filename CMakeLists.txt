cmake_minimum_required(VERSION 2.6)

project(snet-devel)

include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
else()
    message(FATAL_ERROR "Compiler ${CMAKE_CXX_COMPILER} has no C++11 support.")
endif()

# Add custom cxx flags
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -Wall -Wextra")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -Wall -Wextra")

# Automatically set the version number
set(SNET_DEVEL_VERSION_MAJOR  \"1\")
set(SNET_DEVEL_VERSION_MINOR  \"2pre\")
include_directories("${PROJECT_BINARY_DIR}/src")
configure_file (
    "${PROJECT_SOURCE_DIR}/src/SnetConfig.h.in"
    "${PROJECT_SOURCE_DIR}/src/SnetConfig.h"
)

add_subdirectory(src)
