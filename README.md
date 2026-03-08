# STM32 Embedded Systems Learning Portfolio

This repository documents a structured series of embedded firmware projects built on the **STM32 NUCLEO-F446RE** development board.  

The goal of these projects is to demonstrate practical embedded systems skills including:

- register-level programming
- interrupt-driven firmware
- hardware timer configuration
- external interrupts
- peripheral control
- structured firmware development

The projects increase in complexity and build upon each other to illustrate how real embedded systems evolve from simple GPIO control to event-driven firmware architectures.

---

# Hardware Platform

Development Board  
STM32 NUCLEO-F446RE

Microcontroller  
STM32F446RET6

Core  
ARM Cortex-M4

Clock Configuration  
84 MHz system clock

Debug Interface  
ST-LINK (SWD)

Onboard Components Used

| Component | Pin |
|----------|------|
| LD2 LED | PA5 |
| B1 User Button | PC13 |

Development Environment

- STM32CubeIDE
- STM32CubeMX
- ARM GCC Toolchain
- ST-LINK Debugger

---

# Learning Focus

These projects emphasize **understanding what the hardware is doing**, not just writing working code.

Key concepts practiced include:

- memory-mapped register access
- GPIO configuration
- atomic GPIO operations (BSRR)
- hardware timers
- interrupt service routines
- NVIC interrupt routing
- EXTI external interrupts
- firmware architecture patterns

---

# Project Progression

| Project | Topic | Key Concepts |
|-------|------|--------------|
| 01 | Register-Level LED Blink | GPIO registers, BSRR, direct hardware control |
| 02 | Timer Interrupt LED Blink | hardware timers, prescaler math, ISR |
| 03 | Multiple Timer Events | software timers, multi-rate scheduling |
| 04 | Button Interrupt LED Toggle | EXTI, NVIC, event-driven firmware |

Each project builds on the previous one to gradually introduce more advanced embedded concepts.

---

# Repository Structure

embedded-systems-portfolio/
│
├── project01_register_level_blink/
├── project02_timer_interrupt_blink/
├── project03_multiple_timer_events/
├── project04_button_interrupt_led_toggle/
│
└── docs/


Each project folder contains:

- project README
- engineering notes
- STM32CubeMX configuration file (.ioc)
- firmware source code
- optional images or diagrams

---

# Firmware Development Workflow

Typical development workflow for each project:

1. Configure hardware in **STM32CubeMX**
2. Generate project in **STM32CubeIDE**
3. Implement firmware logic in `main.c`
4. Build project
5. Flash firmware using **ST-LINK**
6. Debug and verify hardware behavior

---

# Purpose of This Repository

This repository serves two roles:

1. **Engineering portfolio** demonstrating embedded firmware development.
2. **Structured learning record** documenting embedded systems concepts through hands-on projects.

The code and documentation are intended to show both **technical understanding and development discipline**.

---

# Future Projects

Upcoming projects in this series will include:

- UART serial communication
- interrupt-driven UART reception
- ADC sensor input
- PWM motor/LED control
- I2C peripheral communication
- SPI communication
- DMA transfers
- simple embedded task scheduling

These projects will continue expanding the firmware architecture toward more realistic embedded applications.
