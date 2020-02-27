cmake_minimum_required(VERSION 3.15)
project(WeSing)

set(CMAKE_CXX_STANDARD 14)

# Source files
set(SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/source")
set(LIB_DIR "${CMAKE_CURRENT_SOURCE_DIR}/libraries")

# Including GLFW
add_subdirectory(glfw)
include_directories(glfw/include)

set(SOURCE_FILES main.cpp)

add_executable(${PROJECT_NAME} ${SOURCE_FILES})

#find_package(OpenGL REQUIRED)

# Linking GLFW
#target_link_libraries(${PROJECT_NAME} glfw ${GLFW_LIBRARIES} OpenGL::GL)
target_link_libraries(${PROJECT_NAME} glfw ${GLFW_LIBRARIES})
# glad
set(GLAD_DIR "${LIB_DIR}/glad")
add_library("glad" "${GLAD_DIR}/src/glad.c")
target_include_directories("glad" PRIVATE "${GLAD_DIR}/include")
target_include_directories(${PROJECT_NAME} PRIVATE "${GLAD_DIR}/include")
target_link_libraries(${PROJECT_NAME} "glad" "${CMAKE_DL_LIBS}")