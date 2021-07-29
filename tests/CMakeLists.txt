project (${PROJECT_NAME}_UnitTest)

add_executable(${PROJECT_NAME} "")

# Fetch google test for project **********************************************

include(FetchContent)

FetchContent_Declare (googletest  GIT_REPOSITORY https://github.com/google/googletest.git  GIT_TAG release-1.11.0 )
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

target_compile_definitions(${PROJECT_NAME} PRIVATE -D_SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING)

# adding target sources ******************************************************


target_sources (${PROJECT_NAME} PRIVATE
    "${CMAKE_CURRENT_LIST_DIR}/main.cpp"
    "${CMAKE_CURRENT_LIST_FILE}")

# include other headerfiles **************************************************

target_include_directories (${PROJECT_NAME} PRIVATE "${CMAKE_CURRENT_LIST_DIR}/../source")

# link with libraries ********************************************************

target_link_libraries(${PROJECT_NAME} utils_lib)
target_link_libraries(${PROJECT_NAME} gtest_main gmock_main)

# setup testing **************************************************************

include(GoogleTest)
gtest_add_tests(${PROJECT_NAME} "" AUTO)
