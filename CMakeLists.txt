# Specify CMAKE_PREFIX_PATH to point to you llvm-mos compiler directory before running!
#  like this: "-DCMAKE_PREFIX_PATH=<PATH>/development/llvm-mos"
# for vscode you can use settings.json file located in project root ".vscode" directory
# like this:
#   {
#     "cmake.configureArgs": [
#        "-DCMAKE_PREFIX_PATH=<PATH>/development/llvm-mos"
#     ],
#   }

set(PROJECT_NAME TEMPLATE)
set(ENTRY_FILE main.cpp)
set(LLVM_MOS_PLATFORM cx16)
set(CMAKE_CXX_FLAGS "-gdwarf-4 -g -fno-lto -fcolor-diagnostics -fno-crash-diagnostics -Oz -Wall -Wextra -Wno-uninitialized")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ../bin)

include_directories("${CMAKE_PREFIX_PATH}/mos-platform/common/include/**") 
include_directories("${CMAKE_PREFIX_PATH}/mos-platform/cx16/include/**") 

cmake_minimum_required(VERSION 3.18)
find_package(llvm-mos-sdk REQUIRED)
project(${PROJECT_NAME}) 
add_executable(${PROJECT_NAME}.PRG ${ENTRY_FILE})


