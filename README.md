# Android 2D Game Engine with LuaJIT

This project provides a basic structure for a 2D game engine targeting Android, utilizing LuaJIT for high-performance scripting and game logic.

## Project Structure

The project is organized as follows:

- **`core/`**: Contains the core C++ source code for the engine. This is where the heavy lifting happens (rendering, input handling, audio).
- **`platform/`**: Contains platform-specific code and project files.
  - **`platform/android/`**: The Android Studio project structure.
- **`scripts/`**: Lua scripts for game logic.
  - `main.lua`: The entry point for the Lua side of the engine.
- **`assets/`**: Game assets such as images, sounds, fonts, etc.
- **`thirdparty/`**: External libraries.
  - `luajit/`: Place the LuaJIT library/source here.

## Getting Started

### Prerequisites

- Android Studio / Android SDK / NDK
- CMake (for building the C++ core)
- LuaJIT

### Setup

1.  **LuaJIT Integration**:
    - Download and build LuaJIT for Android (ARMv7, ARM64, x86, x86_64).
    - Place the headers and built static libraries (`.a` files) in `thirdparty/luajit/`.

2.  **Building**:
    - Open `platform/android/` in Android Studio.
    - Configure the NDK path.
    - Build and run the project on an emulator or device.

## Scripting

Game logic is written in Lua. The engine expects `scripts/main.lua` to define basic lifecycle functions:

```lua
function init()
    -- Called once at startup
end

function update(dt)
    -- Called every frame with delta time
end

function draw()
    -- Called every frame to render
end
```

## Architecture

The C++ core initializes the LuaJIT VM and binds necessary native functions (rendering, input) to Lua. The main loop runs in C/C++, calling into Lua for `update` and `draw` callbacks.
