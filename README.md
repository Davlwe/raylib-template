# 🎮 Raylib Game Template

A clean, cross-platform starter template for [raylib](https://www.raylib.com/) projects using CMake. Clone and build in under a minute on macOS, Windows, or Linux.

**What you get:** A window that opens, renders "Hello Raylib!", and runs at 60 FPS. Replace `src/main.cpp` with your own game logic.

---

## Quick Start

```bash
# 1. Install raylib (pick your platform below)
# 2. Build
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build

# 3. Run
./build/game          # macOS / Linux
.\build\game.exe      # Windows
```

**That's it.** Two CMake commands, one to configure, one to build.

---

## Prerequisites

| What | Version | Check |
|---|---|---|
| CMake | ≥ 3.16 | `cmake --version` |
| raylib | ≥ 5.0 | See platform instructions below |
| C++ compiler | C++17 | `g++ --version` or `clang++ --version` |

---

## Platform Setup

### 🍎 macOS

```bash
# Install raylib + cmake (one command)
brew install raylib cmake

# Build
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build

# Run
./build/game
```

> **Apple Silicon (M1/M2/M3):** Homebrew installs to `/opt/homebrew` — CMake finds it automatically.
> **Intel Mac:** Homebrew installs to `/usr/local`. Tell CMake with `-DCMAKE_PREFIX_PATH=/usr/local`.

---

### 🐧 Linux

```bash
# Install raylib + cmake
sudo apt install libraylib-dev cmake g++          # Debian / Ubuntu
sudo dnf install raylib-devel cmake g++            # Fedora
sudo pacman -S raylib cmake gcc                    # Arch

# Build
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build

# Run
./build/game
```

---

### 🪟 Windows (MSYS2)

Open a **UCRT64** terminal and run:

```bash
# Install raylib + build tools
pacman -S mingw-w64-ucrt-x86_64-raylib \
          mingw-w64-ucrt-x86_64-cmake \
          mingw-w64-ucrt-x86_64-gcc

# Build
cmake -S . -B build -G "MinGW Makefiles" -DCMAKE_BUILD_TYPE=Debug
cmake --build build

# Run
./build/game.exe
```

---

### 🪟 Windows (vcpkg — alternative)

```powershell
# Install raylib via vcpkg
vcpkg install raylib:x64-windows

# Build
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=<vcpkg-root>/scripts/buildsystems/vcpkg.cmake
cmake --build build --config Debug

# Run
.\build\Debug\game.exe
```

---

## Project Structure

```
├── CMakeLists.txt          # Build system (cross-platform)
├── README.md               # You are here
├── .gitignore
├── src/
│   └── main.cpp            # Game code — start here
├── build/                  # CMake output (gitignored)
└── .vscode/                # Optional VSCode support
    ├── extensions.json     # Recommended extensions
    ├── settings.json       # CMake defaults
    └── launch.json         # F5 → build + debug
```

---

## Building from Scratch

Writing your own game? Here's the minimum `CMakeLists.txt`:

```cmake
cmake_minimum_required(VERSION 3.16)
project(my-game LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)

find_package(raylib REQUIRED)
add_executable(my-game src/main.cpp)
target_link_libraries(my-game PRIVATE raylib)
```

That's the whole build system. Five lines of logic.

---

## VS Code (Optional)

Open the project folder. VSCode will prompt you to install the recommended extensions:

- **CMake Tools** — configure, build, and run from the sidebar
- **C/C++** — IntelliSense and debugging

After installing extensions, CMake Tools auto-configures on open. Press **F5** to build and run with the debugger attached.

No manual tasks. No hardcoded paths. CMake Tools handles everything.

---

## Build Options

| Flag | Purpose |
|---|---|
| `-DCMAKE_BUILD_TYPE=Debug` | Debug build with symbols |
| `-DCMAKE_BUILD_TYPE=Release` | Optimized build |
| `-DCMAKE_PREFIX_PATH=/path/to/raylib` | Tell CMake where raylib lives |
| `-Draylib_USE_STATIC_LIBS=ON` | Link raylib statically |

---

## License

This template is [Unlicense](https://unlicense.org/) — do whatever you want with it. raylib itself is [zlib/libpng](https://github.com/raysan5/raylib/blob/master/LICENSE) licensed.
