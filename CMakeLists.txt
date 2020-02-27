cmake_minimum_required(VERSION 3.15)
project(WeSing)

set(CMAKE_CXX_STANDARD 14)

# Including GLFW
add_subdirectory(glfw)
include_directories(glfw/include)

set(SOURCE_FILES main.cpp)

add_executable(WeSing ${SOURCE_FILES})

find_package(OpenGL REQUIRED)

# Linking GLFW
target_link_libraries(WeSing glfw ${GLFW_LIBRARIES} OpenGL::GL)