# project03_multiple_timer_events

## Objective

Use a single hardware timer interrupt as a **system tick** to drive multiple software-timed events.

This demonstrates how embedded systems schedule multiple tasks from one timer source.

---

## Hardware

Board  
STM32 NUCLEO-F446RE

LED  
LD2 connected to **PA5**

Timer  
TIM2

---

## Concepts Demonstrated

- periodic interrupt scheduling
- software timers
- multi-rate task timing
- interrupt-driven firmware architecture

---

## Timer Configuration

Timer clock

84 MHz

Prescaler

```
PSC = 8399
```

Timer frequency

```
10 kHz
```

Auto-reload

```
ARR = 999
```

Interrupt interval

```
100 ms
```

---

## Software Timer Design

Each interrupt increments a software counter:

```c
tick_100ms++;
```

Longer intervals are derived from this counter.

| Event | Interval |
|------|---------|
| base tick | 100 ms |
| LED toggle | 500 ms |
| counter update | 1 second |

---

## Interrupt Example

```c
tick_100ms++;

if (tick_100ms % 5 == 0)
{
    GPIOA->ODR ^= (1 << 5);
}

if (tick_100ms % 10 == 0)
{
    tick_1s++;
}
```

---

## Result

The LED continues blinking every 500 ms, while the firmware now tracks multiple periodic events.
