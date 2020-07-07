cmake_minimum_required(VERSION 3.10)
project(restbed)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Notify CMake that we have module files to find packages/libs.
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/modules/")

find_package(PAM REQUIRED)

# Check if we found PAM.
if (NOT PAM_FOUND)
    message(FATAL_ERROR "PAM library was not found.")
endif ()

# Source configuration.
include_directories(
   ${PAM_INCLUDE_DIR}
   ${CMAKE_BINARY_DIR}
   ${CMAKE_CURRENT_BINARY_DIR}
)

set(EXECUTABLE_NAME "application")

# Add sources to this project's executable.
add_executable(${EXECUTABLE_NAME})

target_link_libraries(${EXECUTABLE_NAME}
    ${PAM_LIBRARIES}
)

set_target_properties(${EXECUTABLE_NAME} PROPERTIES LINKER_LANGUAGE CXX)