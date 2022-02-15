cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Block)

# add the executables
add_executable(cmake_static_block program.c)

# add the executables
add_executable(cmake_dynamic_block program.c)

set(SOURCE_PATH "./source")
set(HEADER_PATH "./headers")

# make libraries
add_library(cmake_libblock_static STATIC ${SOURCE_PATH}/block.c ${HEADER_PATH}/block.h)
add_library(cmake_libblock_shared SHARED ${SOURCE_PATH}/block.c ${HEADER_PATH}/block.h)

target_link_libraries(cmake_static_block cmake_libblock_static)
target_link_libraries(cmake_dynamic_block cmake_libblock_shared)