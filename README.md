Part 2:
  1. When an external interrupt occurs, a GPIO pin sets the EXTI pending flag for the NVIC to handle. Then the current main program is stalled whenever the interrupt is enabled, with the hardware pushing registers R0-R3, R12, LR, PC, and PSR onto the stack. Then the ISR gets executed. Before the ISR completes, the EXTI pending flag must be cleared otherwise the ISR can fire indefinitely. When the ISR runs it sets a flag. After the ISR completes the registers are popped off the stack and main resumes. 

Part 3:
  1. The clock register counts the passage of time, with the prescaler dividing the frequency. The timer compares the value in the clock register with the ARR, and when they match the ISR gets fired. The difference between the two is the source of the interrupt, one comes from a pin outside the chip and can come at any time, the other comes from within the chip which occurs at fixed intervals of time.  
  2. ARR = 999, PSC = 15999
