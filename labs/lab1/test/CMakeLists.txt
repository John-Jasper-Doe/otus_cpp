cmake_minimum_required(VERSION 3.2)

set(CMAKE_FOLDER "${CMAKE_FOLDER}/labs/lab1/test")
set(LAB_ONE_TEST_NAME test_version)

add_executable(${LAB_ONE_TEST_NAME} test_version.cpp)
add_test(${LAB_ONE_TEST_NAME} ${LAB_ONE_TEST_NAME})

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
  set_target_properties(${LAB_ONE_TEST_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-g;-O0"
  )
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
  set_target_properties(${LAB_ONE_TEST_NAME}
    PROPERTIES
      CXX_STANDARD 14
      CXX_STANDARD_REQUIRED ON
      COMPILE_OPTIONS "-Wall;-Werror;-Wextra;-Wpedantic;-O2"
  )
endif()

set_target_properties(${LAB_ONE_TEST_NAME}
  PROPERTIES
    COMPILE_DEFINITIONS BOOST_TEST_DYN_LINK
    INCLUDE_DIRECTORIES ${Boost_INCLUDE_DIR}
)
target_include_directories(${LAB_ONE_TEST_NAME} PRIVATE ${COMMON_INCLUDE_PATHS})

target_link_libraries(${LAB_ONE_TEST_NAME}
  ${Boost_LIBRARIES}
  version
)
