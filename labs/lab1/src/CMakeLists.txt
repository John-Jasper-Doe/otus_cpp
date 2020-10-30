cmake_minimum_required(VERSION 3.2)

set(CMAKE_FOLDER "${CMAKE_FOLDER}/labs/lab1/src")

print("Create \"${PROJECT_NAME}\" module on \"${CMAKE_BUILD_TYPE}\" mode")
add_executable(${PROJECT_NAME} "main.cpp")

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
  set_target_properties(${PROJECT_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-g;-O0"
  )
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
  set_target_properties(${PROJECT_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-O2"
  )
endif()

target_include_directories(${PROJECT_NAME} PRIVATE ${COMMON_INCLUDE_PATHS})
target_link_libraries(${PROJECT_NAME}
  version
)

