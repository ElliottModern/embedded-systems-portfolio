# project02_timer_interrupt_blink

## Objective

Blink the onboard LD2 LED using a **hardware timer interrupt** instead of a software delay loop.

This demonstrates how embedded systems use timer peripherals to generate precise periodic events.

---

## Hardware

Board
STM32 NUCLEO-F446RE

LED
LD2 connected to **PA5**

Timer Used
TIM2

---

## Concepts Demonstrated

- hardware timers
- prescaler configuration
- auto-reload registers
- timer interrupts
- NVIC interrupt controller
- interrupt service routines (ISR)

---

## Timer Design

Timer clock

84 MHz

Prescaler

```
PSC = 8399
```

Timer frequency

```
84 MHz / (8399 + 1) = 10 kHz
```

Timer tick

```
100 µs
```

Auto-reload value

```
ARR = 4999
```

Interrupt interval

```
5000 × 100 µs = 500 ms
```

---

## Interrupt Workflow

Timer overflow generates an interrupt:

```
TIM2 overflow
      ↓
NVIC interrupt
      ↓
TIM2_IRQHandler()
      ↓
LED toggled
```

---

## Core Code

Interrupt handler:

```c
void TIM2_IRQHandler(void)
{
    if (TIM2->SR & (1 << 0))
    {
        TIM2->SR &= ~(1 << 0);
        GPIOA->ODR ^= (1 << 5);
    }
}
```

---

## Result

The LED toggles every **500 ms**, producing a **1 second blink cycle**.

The CPU remains idle while the timer runs independently.
