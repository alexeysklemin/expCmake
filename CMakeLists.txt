#required version cvake
cmake_minimum_required(VERSION 3.25)
#project name
project(experimentCmake)
#set standart version
set(CMAKE_CXX_STANDARD 11)
#standart required true
set(CMAKE_CXX_STANDARD_REQUIRED True)

#set first level dir project
set(PRJ_HRR_DIR inc)
set(PRJ_SRC_DIR src)

file(GLOB_RECURSE HEADERS "${CMAKE_SOURCE_DIR}/${PRJ_HRR_DIR}/*.h"
file(GLOB_RECURSE SOURSES "${CMAKE_SOURCE_DIR/${PRJ_SRC_DIR}}/*cpp")

#make executable
add_executable(${PROJECT_NAME}
               ${SOURCES}
               ${HEADERS}
)

#include some library
find_package(libzip REQUIRED)
tasrget_link_libraries(${PROJECT_NAME} PUBLIC ${LIBZIP_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${LIBZIP_INCLUDE_DIR})
