# define project name ********************************************************
project (${PROJECT_NAME}Lib)

# define lib project *********************************************************

add_library(${PROJECT_NAME} STATIC "")

# define target source *****************************************************

target_sources (${PROJECT_NAME} PUBLIC
   "${CMAKE_CURRENT_LIST_DIR}/dummy.cpp"
   "${CMAKE_CURRENT_LIST_FILE}")

# target current path source directory for include ***************************
   
target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_CURRENT_LIST_DIR}/")

# define target compile features and definitions ***************************

target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_14)

