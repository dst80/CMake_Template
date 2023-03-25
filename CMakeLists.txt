cmake_minimum_required (VERSION 3.15)
project (TemplateProject)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/external/modules/")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

option (PACKAGE_TESTS "Build with Tests" ON)

# add project subdirectories hier

add_subdirectory ("source")

if (${PACKAGE_TESTS})
    enable_testing()
    add_subdirectory (tests)
endif()

add_custom_target(
    copy-compile-commands ALL
    ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_BINARY_DIR}/compile_commands.json
    ${CMAKE_CURRENT_LIST_DIR})
