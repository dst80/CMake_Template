project (${PROJECT_NAME}_UnitTest)

# Fetch google test for project **********************************************

include(FetchContent)
FetchContent_Declare (googletest  GIT_REPOSITORY https://github.com/google/googletest.git  GIT_TAG release-1.11.0 )
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

# create test executable *****************************************************

add_executable(${PROJECT_NAME} "")

# adding target sources ******************************************************

target_sources (${PROJECT_NAME} PRIVATE
    "${CMAKE_CURRENT_LIST_DIR}/main.cpp"
    "${CMAKE_CURRENT_LIST_FILE}")

# include other headerfiles **************************************************

target_include_directories (${PROJECT_NAME} PRIVATE "${CMAKE_CURRENT_LIST_DIR}/../source")

# define compiler features and definitions ***********************************

target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_14)

target_compile_definitions(${PROJECT_NAME} PRIVATE -D_SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING)

# link with libraries ********************************************************

target_link_libraries(${PROJECT_NAME} utils_lib)

target_link_libraries(${PROJECT_NAME} gtest_main gmock_main)

# setup testing **************************************************************

include(GoogleTest)
gtest_add_tests(${PROJECT_NAME} "" AUTO)
