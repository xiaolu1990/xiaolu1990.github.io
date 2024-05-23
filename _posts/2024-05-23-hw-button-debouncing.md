---
title: Push Button Debouncing Techniques
tags: [Hardware, Electronics Design, Firmware]
style: border
color: info
description: Introduce several methods to eliminate the "bounce" effect when using push buttons.
---

When using a tactile switch as an input source, it is common that ["button bouncing"](https://deepbluembedded.com/arduino-button-debouncing/) happens without any debouncing methods. 

In this post, I want to share some experiments I have done for validating the different methods, as well as introduce some online tools.

# Test Environment
The experiment is performed on a [Seeeduino Nao](https://wiki.seeedstudio.com/Seeeduino-Nano/) board, where pin `D3` is connected to a push button, and a red LED is connected to pin `D10` as an indicator. Both signals are monitored by the oscilloscope. Here's the setup:

{% include elements/figure.html image="/assets/images/2024-05-23/hw_setup.jpg" caption="Hardware Setup" %}

And the test code:
```cpp
/**
 * @file main.cpp
 * @author Zhangshun Lu
 * @brief A simple I/O test. Once the tacticle switch is pressed, the LED will change the state. The example is using interrupt on falling edge to detect button input. The example is tested on Seeeduino Nano board.
 *        
 * @version 0.1
 * @date 2024-05-23
 * 
 * @copyright Copyright (c) 2024
 * 
 */

#include <Arduino.h>

#define PIN_BTN     3
#define PIN_LED_R   10

volatile byte state = LOW;

void blink();

void setup() {
  pinMode(PIN_LED_R, OUTPUT);
  pinMode(PIN_BTN, INPUT_PULLUP);
  attachInterrupt(digitalPinToInterrupt(PIN_BTN), blink, FALLING);

  digitalWrite(PIN_LED_R, LOW);
}

void loop() {
  digitalWrite(PIN_LED_R, state);
}

/**
 * @brief ISR
 * 
 */
void blink() {
  state = !state;
}
```

# Debouncing using RC Filter Circuit
I first tested the RC filter circuit, this method is handy and cost effective.

{% include elements/figure.html image="https://protological.com/wp-content/uploads/2014/11/debounce.png" caption="RC Filter Circuit" %}

I use the [Debounce calaculator](https://protological.com/debounce-calaculator/) to find out the proper RC value pair. In this experiment, I use 10k for R, and 0.1uF for C.

From the oscilloscope (1=button input, 2=led output), we can see that there is a false detect which happens on the rising edge on the push button. This is not correct because in the code I am using the falling edge as the interrupt source. 

{% include elements/figure.html image="/assets/images/2024-05-23/scope_before.png" caption="False contact due to switch bounce" %}

Then I build the debouncing circuit using the values above, and it looks good 👍.
{% include elements/figure.html image="/assets/images/2024-05-23/scope_after.png" caption="Measurement RC debouncing" %}

# Links
1. [Arduino Button Debouncing Techniques](https://deepbluembedded.com/arduino-button-debouncing/)
2. [Debounce calaculator](https://protological.com/debounce-calaculator/)
3. [Arduino Interrupts](https://www.arduino.cc/reference/en/language/functions/external-interrupts/attachinterrupt/)