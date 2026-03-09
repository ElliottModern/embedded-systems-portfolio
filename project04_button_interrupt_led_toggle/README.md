# project04_button_interrupt_led_toggle

## Objective

Use an external interrupt from the user button to toggle the LED.

This demonstrates event-driven firmware using the STM32 EXTI interrupt system.

---

## Hardware

Board  
STM32 NUCLEO-F446RE

LED  
LD2 connected to **PA5**

User Button  
B1 connected to **PC13**

---

## Concepts Demonstrated

- GPIO external interrupts
- EXTI interrupt controller
- NVIC interrupt routing
- interrupt callbacks
- event-driven firmware

---

## Button Characteristics

Pin

```
PC13
```

Signal behavior

```
Released → HIGH
Pressed → LOW
```

Interrupt trigger

```
Falling edge
```

---

## Interrupt Path

```
Button Press
     ↓
GPIO PC13
     ↓
EXTI line 13
     ↓
NVIC interrupt
     ↓
EXTI15_10_IRQHandler()
     ↓
HAL_GPIO_EXTI_Callback()
     ↓
LED toggled
```

---

## Callback Implementation

```c
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
    if (GPIO_Pin == GPIO_PIN_13)
    {
        GPIOA->ODR ^= (1 << 5);
    }
}
```

---

## Result

Each button press toggles the LED state:

```
Press 1 → LED ON
Press 2 → LED OFF
Press 3 → LED ON
```

The system now reacts to **external hardware events instead of periodic timers**.
