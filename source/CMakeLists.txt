# define project name ********************************************************
project (TemplateProjectLib)

# define lib project *********************************************************
add_library(${PROJECT_NAME} STATIC "")


# adding target source subdirectories ****************************************

# current path source directory **********************************************

target_sources (${PROJECT_NAME} PUBLIC
   "${CMAKE_CURRENT_LIST_DIR}/dummy.cpp"
   "${CMAKE_CURRENT_LIST_FILE}")

# target current path source directory for include ***************************

target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_CURRENT_LIST_DIR}/")
