---
title: LVGL Setup
tags: [Coding]
style: border
color: secondary
description: How to integrate LVGL in different platforms
---

This post explains how to set up an LVGL development environment on different platforms.

# Run LVGL on Windows (MinGW toolchain)
This section shows how to run LVGL in a simulator using VS Code on Windows.

Template source code: [lv_port_pc_vscode](https://github.com/xiaolu1990/lv_port_pc_vscode/tree/main)

Follow these steps:
1. Install the MinGW-w64 compiler toolchain, then add MinGW to your `PATH`.

   Verify the installation:
   - `gcc --version`
   - `g++ --version`

2. Install CMake.

   Verify the installation:
   - `cmake --version`

3. Install SDL2 for MinGW by following [the official guide](https://github.com/libsdl-org/SDL/blob/main/docs/INTRO-mingw.md).

   Open the `MSYS2 UCRT64` command prompt and run:

   ```sh
   pacman -S mingw-w64-ucrt-x86_64-gcc mingw-w64-ucrt-x86_64-ninja mingw-w64-ucrt-x86_64-cmake
   pacman -S mingw-w64-ucrt-x86_64-SDL2
   ```

4. Clone the official LVGL PC simulator repository, [lv_port_pc_vscode](https://github.com/lvgl/lv_port_pc_vscode), into your workspace.

5. In `CMakeLists.txt`, make sure the following lines are present:

    ```cmake
    # Add LVGL subdirectory
    add_subdirectory(lvgl)
    target_include_directories(lvgl PRIVATE ${PROJECT_SOURCE_DIR} ${SDL2_INCLUDE_DIRS})
    ```

6. Update the `launch` section in `simulator.code-workspace`:

   ```json
   // launch.json section
   "launch": {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Debug LVGL demo with gdb",
         "type": "cppdbg",
         "request": "launch",
         "program": "${workspaceFolder}/bin/main",
         "args": [],
         "cwd": "${workspaceFolder}",
         "preLaunchTask": "Build",
         "stopAtEntry": false,
         "linux": {
           "MIMode": "gdb",
           "miDebuggerPath": "/usr/bin/gdb"
         },
         "osx": {
           "MIMode": "lldb"
         },
         "windows": {
           "MIMode": "gdb",
           "miDebuggerPath": "C:\\msys64\\ucrt64\\bin\\gdb.exe" // path to gdb.exe
         }
       }
     ]
   }
   ```

7. Start debugging with the `Debug LVGL demo with gdb` configuration.

# Run LVGL on an embedded display (Waveshare ESP32-S3-Touch-LCD-2.1)
This section covers LVGL setup for the [Waveshare ESP32-S3-Touch-LCD-2.1](https://www.waveshare.com/esp32-s3-touch-lcd-2.1.htm?srsltid=AfmBOoqbHMnMtkDNZLYD6vi-eYB_j_kwCMnk5fjM43YxKZc3xkcP4K8y).

Template source code: [lv_port_waveshare_esp32_s3](https://github.com/xiaolu1990/lv_port_waveshare_esp32_s3)

Follow these steps to kick off:
1. Install the prerequisites:
  - VS Code
  - PioArduino VS Code extension
  > Why PioArduino? 
  > See this discussion: <https://github.com/platformio/platform-espressif32/issues/1225>

2. Clone the repository [lv_port_waveshare_esp32_s3](https://github.com/xiaolu1990/lv_port_waveshare_esp32_s3).

3. Build and flash the device with the PioArduino toolchain.