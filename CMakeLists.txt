cmake_minimum_required (VERSION 3.15)
project (TemplateProject)

set (CMAKE_CXX_STANDARD 14)
set (CMAKE_CXX_STANDARD_REQUIRED ON)
set (CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/external/modules/")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if(MSVC)
    string(REGEX REPLACE "/W[1-3]" "/W4" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
else()
    add_compile_options("-Wall" "-Wextra" "-Werror" "-pedantic" "$<$<CONFIG:RELEASE>:-O3>")
endif()

option (PACKAGE_TESTS "Build with Tests" ON)


# add project subdirectories hier

add_subdirectory ("source")

if (${PACKAGE_TESTS})
    add_subdirectory (tests)
endif()
