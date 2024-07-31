cmake_minimum_required(VERSION 3.0...3.25)

project(
    raycast
    VERSION 0.1.0
    LANGUAGES CXX C
)

add_executable(raycast src/main.cpp)

set_target_properties(raycast PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
    CXX_EXTENSIONS OFF
    COMPILE_WARNING_AS_ERROR ON
)

if (MSVC)
    target_compile_options(raycast PRIVATE /W4)
else()
    target_compile_options(raycast PRIVATE -Wall -Wextra -pedantic)
endif()

if (XCODE)
    set_target_properties(raycast PROPERTIES
        XCODE_GENERATE_SCHEME ON
        XCODE_SCHEME_ENABLE_GPU_FRAME_CAPTURE_MODE "Metal"
    )
endif()
