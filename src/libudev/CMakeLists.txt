cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

set(PROJ udev)
PROJECT(${PROJ})

set(CMAKE_C_FLAGS "-Wall -pthread")
set(CMAKE_C_FLAGS_DEBUG "-g -O0")
set(CMAKE_C_FLAGS_RELEASE "-O3")
set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -std=c++14 -lstdc++")
set(CMAKE_CXX_FLAGS_DEBUG ${CMAKE_C_FLAGS_DEBUG})
set(CMAKE_CXX_FLAGS_RELEASE ${CMAKE_C_FLAGS_RELEASE})

add_definitions(-DRELATIVE_SOURCE_PATH="./")


FILE(GLOB SRC_FILES
        ./*.c
        ./*.h
    )
add_library(${PROJ} SHARED
    ${SRC_FILES}
  )
target_include_directories(${PROJ} PRIVATE
    .
    ../../src/basic/
    ../../src/systemd/
    ../../src/libsystemd/sd-device/
    ../../src/systemd/src/systemd/
    )

