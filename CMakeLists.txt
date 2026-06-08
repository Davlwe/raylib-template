cmake_minimum_required(VERSION 3.16)
project(raylib-game VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# ---- Find raylib ----
# Uses raylib's own CMake config. If CMake can't find raylib, tell it
# where to look by passing -DCMAKE_PREFIX_PATH=<your-raylib-prefix>
# at configure time (see README.md for platform-specific examples).
find_package(raylib REQUIRED)

if(NOT raylib_FOUND)
    message(FATAL_ERROR
        "raylib not found.\n"
        "Install raylib first, then try again.\n"
        "See README.md for platform-specific setup instructions."
    )
endif()

# ---- Executable ----
add_executable(game src/main.cpp)
target_link_libraries(game PRIVATE raylib)
