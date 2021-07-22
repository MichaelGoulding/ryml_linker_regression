cmake_minimum_required (VERSION 3.16)

project (ryml_linker_regression)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(ryml)


add_library(sampleDll SHARED
    file1.cpp
    file2.cpp
    shared.h
)

target_link_libraries(sampleDll PRIVATE ryml::ryml)
target_compile_options(sampleDll PRIVATE -W4 -WX)

#this is the workaround
#target_link_options(sampleDll PRIVATE /FORCE:MULTIPLE)