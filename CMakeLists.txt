cmake_minimum_required(VERSION 3.15)
project(WeSing)

set(CMAKE_CXX_STANDARD 14)

# Source files
set(SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src")
set(LIB_DIR "${CMAKE_CURRENT_SOURCE_DIR}/libraries")

set(SOURCE_FILES "${SRC_DIR}/main.cpp")

add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# Including GLFW
add_subdirectory(${LIB_DIR}/glfw)
include_directories(${LIB_DIR}/glfw/include)

# Linking GLFW
target_link_libraries(${PROJECT_NAME} glfw ${GLFW_LIBRARIES})

# glad
set(GLAD_DIR "${LIB_DIR}/glad")
add_library("glad" "${GLAD_DIR}/src/glad.c")
target_include_directories("glad" PRIVATE "${GLAD_DIR}/include")
target_include_directories(${PROJECT_NAME} PRIVATE "${GLAD_DIR}/include")
target_link_libraries(${PROJECT_NAME} "glad" "${CMAKE_DL_LIBS}")

#inipp
include_directories("${LIB_DIR}/inipp")