---
title: STM32 Solutions for Advanced GUI Applications
tags: [STM32, Hardware]
style: border
color: success
description: STM32 MCUs for advanced GUI application solutions.
---
Running GUI applications on MCU is more and more popular. But there is still a problem, since most MCUs don't have dedicated GPU to process the graphics, and this job is much relied on the LCD driver IC, running complex UI on MCU is not easy. It will be much harder if you want to drive a display with high resolution, because that requires a lot of RAM sapce. And that's why, most MCUs based GUI applications only work with small disaplays (small physical size displays usually have lower resolution as well).

But this is not the end, STMicroelectronics offers several MCU products that has integrated GPU, they offer enhanced performance and advanced graphics capability.

In this post, I will bring 3 MCUs to front, which are STM32F7x9, STM32H7x7 and STM32U5x9.

## STM32F7x9 MCU
[STM32F7x9](https://www.st.com/en/microcontrollers-microprocessors/stm32f7x9.html) lines offer the performance of Cortex-M7 core running up to 216 MHz. To design GUI applications, a good starting point is to use the official [32F769IDISCOVERY](https://www.st.com/en/evaluation-tools/32f769idiscovery.html#overview) development board. In the discovery kit, the display and the base board is connected via MIPI-DSI interface.

{% include elements/figure.html image="/assets/images/2025-03-24/stm32f7x9_product_line.png" caption="STM32F7x9 Product Portofolio" %}

The MCU has the features of:
1. Arm-Cortex-M7 core, max.frequency 216 MHz.
2. 2 MB Flash and 512 KB RAM.
3. Graphics: DMA 2D, LTDC support up to XGA resolution (1024x768 px.), MIPI-DSI controller support up to 720p@30Hz.

## STM32H7x7 MCU
[STM32H7x7](https://www.st.com/en/microcontrollers-microprocessors/stm32h747-757.html) is a dual-core mcu, which combines the performance of Cortex-M7 running up to 480 MHz and the Cortex-M4 core. Use the official [STM32H747I-DISCO](https://www.st.com/en/evaluation-tools/stm32h747i-disco.html#overview) discovery kit to start learning this MCU. In the discovery kit, the display and the base board is connected via the MIPI-DSI interface.

{% include elements/figure.html image="/assets/images/2025-03-24/stm32h7x7_product_line.png" caption="STM32H7x7 Product Portofolio" %}

The MCU has the feature of:
1. Dual core, Cortex-M7 and Cortex-M4.
2. Up to 2 MB flash and 1 MB RAM.
3. Graphics: DMA 2D, LTDC suppport, MIPI-DSI controller.
4. Compare to STM32H747 series, the STM32H757 MCUs offers additional security features such as Crypto/hash hardware acceleration.

## STM32U5x9 MCU
The STM32U5x9 MCUs belongs to the STM32 ulta-low-power portofolio, while they offer an enhanced performance and advanced graphics capability. They are the first STM32 lines to embed the GPU 2D graphic accelerator, which provides enhanced graphics processing power than the DMA 2D unit.

The MCU has the feature of:
1. Arm Cortex-M33 core running up to 160 MHz.
2. Up to 4 MB flash and 3 MB RAM.
3. Graphics: DMA 2D, GPU 2D, LTDC support, MIP-DSI controller.

The STM32U5x9 MCUs can be further categorized into two product lines, the [STM32U599/U5A9](https://www.st.com/en/microcontrollers-microprocessors/stm32u599-5a9.html) and [STM32U5F9/U5G9](https://www.st.com/en/microcontrollers-microprocessors/stm32u5f9-5g9.html). As shown in the graph below, the STM32U5F9/G9 serie offers the additional vector graphics processing capability in its GPU 2D unit.

{% include elements/figure.html image="/assets/images/2025-03-24/stm32u5_overview.png" caption="STM32U5 MCUs for GUI Application" %}

{% include elements/figure.html image="/assets/images/2025-03-24/stm32u599_product_line.png" caption="STM32U599/U5A9 Product Portofolio" %}

{% include elements/figure.html image="/assets/images/2025-03-24/stm32u5g9_product_line.png" caption="STM32U5F9/U5G9 Product Portofolio" %}

To evaluate STM32U599/U5A9, we can start from the discovery kit [STM32U5A9J-DK](https://www.st.com/en/evaluation-tools/stm32u5A9j-dk.html). Note this one is marked as **NRND**, thus ST recommends to use [STM32U5G9J-DK1](https://www.st.com/en/evaluation-tools/stm32u5g9j-dk1.html) instead. Apart from the ST discovery kits, we can also evaluate the MCUs through the [Riverdi RVT50HQSNWN00](https://riverdi.com/de/product/5-inch-lcd-display-stm32u5-rvt50hqsnwn00).

To evaluate STM32U5F9/U5G9, we can either use the discovery kit [STM32U5G9J-DK1](https://www.st.com/en/evaluation-tools/stm32u5g9j-dk1.html) or [STM32U5G9J-DK2](https://www.st.com/en/evaluation-tools/stm32u5g9j-dk2.html). The difference between these two kits is they are using difference interface between the display and base board, i.e. DK1 is uses MIPI-DSI, DK2 uses RGB888 24-bit parallel.

## Summary
The MCUs mentioned in this post serves for the GUI application, they all come with the embedded GPU with the enhanced graphics processsing capability. STM32F7x9 and STM32H7x7 MCUs have similar GPU implementation, the major difference between the chips lay on the processor. The STM32U5x series features with the ultra-low-power processor, and comes with an enhanced GPU accelerator GPU 2D.

From the perspective of pricing, the STM32U5x has the least unit price, the STM32F7x9 and STM32H7x7 has close unit price.

Since STM32F7x9 has come into the market for several years, it has by far the richest developement resources. 

