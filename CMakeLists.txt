cmake_minimum_required(VERSION 3.28)
project(kotlinscript C)
project(kotlinscript_sys C)

set(CMAKE_C_STANDARD 17)

add_library(kotlinscript base/lib.c)

add_executable(kotlinscript_sys system_runner/main.c)
add_dependencies(kotlinscript_sys kotlinscript)