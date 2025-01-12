cmake_minimum_required(VERSION 3.10.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
aux_source_directory(. DIR_SRCS)
add_executable(planning ${DIR_SRCS})