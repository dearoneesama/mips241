cmake_minimum_required (VERSION 2.8.8)
project(mips-emulator C)

# version
set(mips-emulator_VERSION_MAJOR 0)
set(mips-emulator_VERSION_MINOR 1)

#configure_file(
#    "${PROJECT_SOURCE_DIR}/config.h.in"
#    "${PROJECT_BINARY_DIR}/config.h"
#    )

include_directories(src)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

enable_testing()


if (CMAKE_VERSION VERSION_LESS "3.1")
  set (CMAKE_C_FLAGS "--std=c99 ${CMAKE_C_FLAGS}")
else ()
  set (CMAKE_C_STANDARD 99)
endif ()

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -pedantic")


set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/external/sanitizers-cmake/cmake" ${CMAKE_MODULE_PATH})


add_subdirectory(src)
add_subdirectory(test)
