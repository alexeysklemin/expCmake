#required version cmake
cmake_minimum_required(VERSION 3.23)
#project name
project(expCmake)
#set standart version
set(CMAKE_CXX_STANDARD 11)
#standart required true
set(CMAKE_CXX_STANDARD_REQUIRED True)

#set first level dir project
set(PRJ_HDR_DIR ${CMAKE_CURRENT_SOURCE_DIR}/inc)
set(PRJ_SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

file(GLOB_RECURSE HEADERS "${PRJ_HDR_DIR}/*.h")
file(GLOB_RECURSE SOURCES "${PRJ_SRC_DIR}/*.cpp")
file(GLOB_RECURSE SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/main.cpp")
#stup text
message(STATUS "Find headers PRJ" ${PRJ_HDR_DIR})
message(STATUS "Find headers HEADERS" ${HEADERS})
message(STATUS "Find sources SRC" ${PRJ_SRC_DIR})
message(STATUS "Find sources SOURCES" ${SOURCES})
message(STATUS "Absolute path to header: ${PRJ_HDR_DIR}/depend")

#make executable
add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

#set directories of target
target_include_directories (${PROJECT_NAME} PUBLIC
            "${PRJ_HDR_DIR}/depends"
            "${PRJ_HDR_DIR}"
)

#add own sublibraries or projects
#add_subdirectory("../mylib" mylib)

#include some library
find_package(libzip REQUIRED)
target_link_libraries(${PROJECT_NAME} PUBLIC ${LIBZIP_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${LIBZIP_INCLUDE_DIRS})



