cmake_minimum_required(VERSION 3.2)






# Project name.
# Check if there is an environment variable.
if ($ENV{TRAVIS_BUILD_NUMBER})
  project(helloworld VERSION 0.0.$ENV{TRAVIS_BUILD_NUMBER})
else ($ENV{TRAVIS_BUILD_NUMBER})
  project(helloworld VERSION 0.0.1)
endif ($ENV{TRAVIS_BUILD_NUMBER})


set(COMMON_INCLUDE_PATHS ${CMAKE_BINARY_DIR}/labs/lab1/include)
#set(COMMON_INCLUDE_PATHS ${CMAKE_BINARY_DIR}/labs/lab1/include)


# Search for the "boost" library to enable unit tests.
find_package(Boost COMPONENTS unit_test_framework REQUIRED)

# Configuring a project version file.
configure_file(gen/version.h.in ${COMMON_INCLUDE_PATHS}/version.h)

add_subdirectory(lib)
add_subdirectory(src)
add_subdirectory(test)






install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)

set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

set(CPACK_PACKAGE_CONTACT john.jasper.doe@gmail.com)
set(CPACK_DEBIAN_PACKAGE_SHLIBDEPS ON)

include(CPack)

enable_testing()
