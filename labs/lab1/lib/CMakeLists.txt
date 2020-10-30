cmake_minimum_required(VERSION 3.2)

set(CMAKE_FOLDER "${CMAKE_FOLDER}/labs/lab1/lib")
set(LAB_ONE_LIBRARY_NAME version)

print("Create \"${LAB_ONE_LIBRARY_NAME}\" module on \"${CMAKE_BUILD_TYPE}\" mode")
add_library(${LAB_ONE_LIBRARY_NAME} STATIC "lib.cpp")

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
  set_target_properties(${LAB_ONE_LIBRARY_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-g;-O0"
  )
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
  set_target_properties(${LAB_ONE_LIBRARY_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-O2"
  )
endif()
target_include_directories(${LAB_ONE_LIBRARY_NAME} PRIVATE ${COMMON_INCLUDE_PATHS})

file(COPY "lib.h" DESTINATION ${CMAKE_BINARY_DIR}/labs/lab1/include)
