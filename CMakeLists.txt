# The root "CMakeFile" of this project.
#
# Copyright John Doe 2020
# Distributed under the OSI-approved BSD 3-Clause License. See accompanying
# file LICENSE.txt or https://opensource.org/licenses/BSD-3-Clause for details.

cmake_minimum_required(VERSION 3.8)

# Setting name for this project.
set(PROJECT_NAME otus_cpp_032020)
set(PROJECT_DESCRIPTION "Homework for the course...")

# Adding a path with "cmake" modules to the system search paths.
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Setting up a project.
include(print)
include(function)

project(
  ${PROJECT_NAME}
  DESCRIPTION ${PROJECT_DESCRIPTION}
  LANGUAGES CXX
)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

print("CMAKE_LIBRARY_OUTPUT_DIRECTORY: ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}")
print("CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG: ${CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG}")
print("CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE: ${CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE}")


# Added directory
add_subdirectory(labs)

