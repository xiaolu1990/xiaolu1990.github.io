---
title: STM32 Dev Setup (feat. VSCode + Keil)
tags: [STM32]
style: border
color: info
description: Setup the firmware development environment for STM32 in VSCode.
---

There are multiple toolchains to build a STM32 project. Using [Keil MDK](https://www.st.com/en/partner-products-and-services/arm-keil-mdk.html) is one of the most popular, it provides everything for creating, building and debugging the application. However, the coding experience in the IDE is not very pleasant, such as the auto-completion, file navigation, highlighting etc,. This can be improved by using VSCode with a few setups.

## Steps
1. Install the [**Keil Assistant**](https://github.com/github0null/keil-assistant/blob/master/README_EN.md) plugin in VSCode.
2. Go to the settings of `Keil Assistant`, then update the absolute path of the Keil program.
3. Once installed, the *KEIL UVISION PROJECT* tab should be visible in the file explorer sidebar.
4. Create a project on Keil, add files, header path, etc.
5. Click Open the Project icon and add your keil project file (.uvproj), the keil project will be automatically loaded by the plug-in. 
6. The plugin can automatically refresh the project in VSCode when it detects the changes of the Keil project.

---
## Example
{% include elements/figure.html image="/assets/images/2025-03-07/vscode_keil_example.png" caption="Example of the STM32 Setup: VSCode + Keil" %}

---
## Reference
1. [VSCode Plugin: Keil Assistant](https://github.com/github0null/keil-assistant/blob/master/README_EN.md)
2. [VSCode STM32 开发环境配置](https://www.kiloleaf.com/posts/stm32_development_and_debugging_using_vscode/)