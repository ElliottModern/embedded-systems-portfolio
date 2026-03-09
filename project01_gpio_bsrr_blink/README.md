# project01_register_level_blink

## Objective

Blink the onboard LD2 LED on the STM32 NUCLEO-F446RE using **direct register-level GPIO control**.

This project avoids high-level HAL functions and demonstrates how to manipulate hardware registers directly.

---

## Hardware

Board
STM32 NUCLEO-F446RE

LED
LD2 connected to **PA5**

---

## Concepts Demonstrated

- memory-mapped peripheral registers
- GPIO configuration registers
- atomic GPIO operations using **BSRR**
- direct hardware control in C
- basic embedded delay loops

---

## Core Implementation

The LED is controlled using the **GPIOA BSRR register**, which allows atomic bit set and reset operations.

```c
GPIOA->BSRR = (1U << 5);          // Set PA5 HIGH
GPIOA->BSRR = (1U << (5U + 16U)); // Reset PA5 LOW
```

This avoids race conditions that can occur when using the ODR register.

Delay Implementation

A simple busy-wait delay loop is used:

```c
static void delay(volatile uint32_t count)
{
    while (count--)
    {
        __NOP();
    }
}
```

While functional, this approach blocks the CPU and wastes cycles.

This limitation motivates the next project.

Result

The LED blinks continuously with a visible on/off cycle using direct register writes.
