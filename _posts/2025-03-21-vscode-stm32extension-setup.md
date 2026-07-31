---
title: STM32 Dev Setup (feat. VSCode + STM32 VS Code Extension)
tags: [STM32]
style: border
color: info
description: Setup the firmware development environment for STM32 in VSCode with the STM32 VS Code Extension.
---

Earlier I have written a post about using the [ Keil Assistant ](https://marketplace.visualstudio.com/items?itemName=CL.keil-assistant) extension in VS Code to set up the development environment for STM32. The configuration is easy to accomplish and it uses the ARM Clang complier, which is very effient. However, there are two things that are not convenient:
- For commericial use, you have to afford a license for Keil.
- To debug the program, you have to switch back to Keil.

In this post, I am going to introduce a new toolchain. That is using the [STM32 VS Code Extension](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension) to realize the tasks of edit, build and debug only in VS Code. 

Let's get started! 

## Steps
1. Install the [**STM32 VS Code Extension**](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension) plugin in VSCode. You also have to install [**STM32 CubeMX**](https://www.st.com/en/development-tools/stm32cubemx.html) and [**STM32CubeCLT**](https://www.st.com/en/development-tools/stm32cubeclt.html).
2. Go to the settings of *STM32 VS Code Extension*, update the path of *STM32CubeCLT* and *STM32CubeMX*.
3. Install the [**Arm GNU Toolchain**](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads) and add to the system path.
4. Use *STM32 CubeMX* to create a new project, configure MCU whatever you wish. {% include elements/highlight.html text="IMPORTANT! Set the Toolchain/IDE to CMake." %}

    {% include elements/figure.html image="/assets/images/2025-03-21/cubemx.png" caption="Create a new project from STM32 CubeMX" %}

5. Next, open the STM32 VS Code Extension in VS Code, and import the project.
6. Now, you can call `CMake:Build` to compile the program. Of course, the [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) extension has to be installed.

    {% include elements/figure.html image="/assets/images/2025-03-21/build.png" caption="Build the project" %}

7. The default debug settings is to use the ST-Link debugger. Sending `Stlinkupgrade` in the terminal to ensure the stlink firmware is up to date.
    
    {% include elements/figure.html image="/assets/images/2025-03-21/debug.png" caption="Debug the project" %}

## Summary
Using the **STM32 VS Code Extension** offers several benefits:
1. It leverages **VS Code’s IntelliSense** for advanced code suggestions and navigation.
2. It enables **seamless debugging** using **OpenOCD, ST-Link, or Segger J-Link**.
3. It is cross-platform supported. Which unlike Keil or STM32 CubeIDE has limitted support.