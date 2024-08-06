cmake_minimum_required(VERSION 3.13) # CMake version check
project(app)                         # Create project "app"
set(CMAKE_CXX_STANDARD 20)           # Enable C++20 standard

add_executable(app "src/main.cpp")

set(DAWN_FETCH_DEPENDENCIES ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_subdirectory("dawn" EXCLUDE_FROM_ALL)
target_link_libraries(app PRIVATE webgpu_cpp webgpu_dawn glfw webgpu_glfw)
