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

#stup text
message(STATUS "Find headers " ${PRJ_HDR_DIR})
message(STATUS "Find headers " ${HEADERS})
message(STATUS "Find sources " ${PRJ_SRC_DIR})
message(STATUS "Find sources " ${SOURCES})

#make executable
add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

#set directories of target
target_include_directories (${PROJECT_NAME} PUBLIC
            "${CMAKE_CURRENT_SOURCE_DIR}/${PRJ_HDR_DIR}/depend"
   #         "${CMAKE_CURRENT_SOURCE_DIR}/${PRJ_HDR_DIR}"
)

#add own sublibraries or projects
#add_subdirectory("../mylib" mylib)

#include some library
find_package(libzip REQUIRED)
target_link_libraries(${PROJECT_NAME} PUBLIC ${LIBZIP_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${LIBZIP_INCLUDE_DIRS})

compilation terminated.
make[2]: *** [CMakeFiles/expCmake.dir/build.make:76: CMakeFiles/expCmake.dir/src/depends/depends.cpp.o] Ошибка 1
make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/expCmake.dir/all] Ошибка 2
make: *** [Makefile:91: all] Ошибка 2

