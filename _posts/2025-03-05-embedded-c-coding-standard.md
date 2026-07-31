---
title: Embedded C Coding Standard
tags: [Coding, C]
style: border
color: info
description: Writing firmware in C by following the standard to improve maintainability and portability.
---

During my experience on writing firmware as well as reading reference code by other developers, I have realized the importance of having a good habit on coding style. A good coding style can save lots of time in understanding how the program works and provides an insight into the chip. And later, as more features are required, and the program grows, maintaining the existing code and porting to different platforms could be a tedious task if the coding style is not consistent.
Although there are code formatters which helps formatting the code automatically, it is nice to have a good habit on writing code by keep some rules in mind.

The book *Embedded C Coding Standard* by Michael Barr is a very good guidance that covers the essentials of writing embedded C software. In this post, I have noted down some advices.

---
## General Rules
1. Choose the ISO C Programming Standard and ensure the code you written complies with the standard. In my case, `C99` is selected.
2. Restrict the max. line width of the code, e.g. `80` characters per line.
3. Using `static` to declare functions and variables that are used in the module only, protecting them from external use.
4. Using keywords like `volatile`, `const` whenever appropriate.

```c
// Here is an example of using the keywords 

#define HW_TIMER_ADDR 0x20000000

// Define a const value as the timer register reload value
const uint16_t reloadVal = 500;

typedef struct
{
    uint16_t    count;
    uint16_t    maxCount;
    uint16_t    ctrl;
} timer_reg_t;

// Define a pointer to the timer register
// Keyword `volatile` ensure the variable won't be optimized by the compiler, it indicates that the contents in the register address are changable
// Keyword `const` indicate that the pointer itself is unchangeable, it always points to the base address of the timer register `HW_TIMER_ADDR` 
timer_reg_t volatile * const p_timer = (timer_reg_t *) HW_TIMER_ADDR;

p_timer->maxCount = reloadVal;
```

---
## Comment Rules
1. To temporarily disable a code block, use the precessor's conditional compilation feature e.g. `#if 0 ... #endif`. This is preferrer than commenting out the whole code block.
2. The level of debug output information can be optimized by using the conditional feature as well, e.g. `#ifndef NDEBUG ... #endif`.
3. Using capitalized comment markers such as `WARNING`, `TODO`, `NOTE` to highlight the important issues.
4. Commenting the functions and modules in a right manner with the description of the usage, the meaning of variables. This can be usually done by a plugin in most code editors. 

---
## White Space Rules
1. The `#` shall always be located in the start of the line, though the directives maybe indented within a `#if` or `#ifdef` sequence.

```c
#ifdef USE_EXTERNAL_CLK
#   define SYS_CLK     16000000
#else
#   define SYS_CLK     8000000
#endif
```

---
## Module Rules
1. All module names shall consist entirely of lowercase letters, numbers and underscores. All module names shall be unique in their first 8 characters and end with suffices `.h` and `.c` for the header and source file names respectively. E.g. `system.c`, `system.h`, `adc.c`, `adc.h`, `tmc5160_uart.c`, `tmc5160_uart.h`
2. The header files shall identify only the procedures, constants and data types (via prototypes or macros, `#define` and typedefs respectively).
3. No public header files shall contain a `#include` of any private header file.
4. Each source file shall be comprised of some or all of the following sections, in the order listed:
   1. comment block
   2. include statements
   3. data type, constant, and macro definitions
   4. static data declarations
   5. private function prototypes
   6. public function bodies
   7. priviate function bodies

```c
/*
 * @file_name   example.c   
 * @brief       Example of a source file, comment block goes first
 */

#include "example.h"    // include statements follows next

const uint32_t delay_ms = 1000;  // then data types, constant and macro definitions

#define LED_PIN (10)

static void get_brightness();   // then static function prototypes

void led_init()
{
    // public function bodies
}

static void get_brightness()
{
    // private function bodies
}

```