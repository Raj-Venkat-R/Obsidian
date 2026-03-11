## 1. List the interrupts used in 8051 microcontrollers

8051 has five interrupts:

- External Interrupt 0 (INT0)  
- Timer 0 Interrupt  
- External Interrupt 1 (INT1)  
- Timer 1 Interrupt  
- Serial Port Interrupt  

These interrupts help the CPU respond to external and internal events immediately.



## 2. How register bank is selected in 8051 microcontroller?

Register banks are selected using RS1 and RS0 bits in the PSW register. Depending on these bits, one of the four register banks (Bank0–Bank3) is activated.

| RS1 | RS0 | Register Bank            |
|-----|-----|--------------------------|
| 0   | 0   | Bank 0 (00H–07H)         |
| 0   | 1   | Bank 1 (08H–0FH)         |
| 1   | 0   | Bank 2 (10H–17H)         |
| 1   | 1   | Bank 3 (18H–1FH)         |



## 3. What are the main components of embedded system?

An embedded system consists:

- Microcontroller / Processor  
- Memory (RAM/ROM)  
- Input/Output devices  
- Timers/Counters  
- Communication interfaces  
- Power supply  



## 4. Differentiate microprocessor and microcontroller

| Microprocessor              | Microcontroller                  |
|----------------------------|----------------------------------|
| Only CPU                   | CPU + RAM + ROM + I/O           |
| External peripherals needed| Built-in peripherals             |
| Used in computers          | Used in embedded systems         |
| More power consumption     | Low power                       |



## 5. Sketch the TMOD Table of 8051 for timer operation

| Gate | C/T | M1 | M0 | Mode                    |
|------|-----|----|----|--------------------------|
| x    | 0   | 0  | 0  | Mode 0 (13-bit)          |
| x    | 0   | 0  | 1  | Mode 1 (16-bit)          |
| x    | 0   | 1  | 0  | Mode 2 (8-bit auto reload)|
| x    | 0   | 1  | 1  | Mode 3 (split timer)     |



## 6. Write an 8051 embedded C program to toggle port P1.0

P1.0 can be toggled using an embedded C program with a delay loop.  
An LED connected to P1.0 will blink continuously ON and OFF.

```c
#include <reg51.h>

sbit LED = P1^0;

void delay() {
    int i, j;
    for(i = 0; i < 200; i++)
        for(j = 0; j < 1275; j++);
}

void main() {
    while(1) {
        LED = ~LED;
        delay();
    }
}
```



## 7. Compare RTOS and Operating System

| RTOS            | OS                |
|----------------|-------------------|
| Deterministic  | Non-deterministic |
| Used in embedded | Used in computers |
| Fast response  | General purpose   |
| Task priority based | Time sharing |



## 8. Recall the analog pins in Arduino UNO

Arduino UNO has six analog input pins labeled A0 to A5.  
These pins read varying voltage values from analog sensors.

A0, A1, A2, A3, A4, A5  



## 9. Define Context switching

Context switching is saving the state of one task and loading another task.  
It enables multiple tasks to share the CPU effectively.



## 10. A switch is connected to pin P1.0 and LED to pin P2.7. Write C program to get status of switch and send to LED

The microcontroller reads the switch status from P1.0.  
The same status is sent to P2.7 to turn the LED ON or OFF accordingly.

```c
#include <reg51.h>

sbit SW  = P1^0;
sbit LED = P2^7;

void main() {
    while(1) {
        LED = SW;
    }
}
```



## 11. Name the flags used in 8051 with its significance

| Flag | Bit   | Name                   | Significance                                          |
| ---- | ----- | ---------------------- | ----------------------------------------------------- |
| CY   | PSW.7 | Carry Flag             | Set when arithmetic operation generates carry/borrow  |
| AC   | PSW.6 | Auxiliary Carry        | Set when carry from D3 to D4 (used in BCD operations) |
| F0   | PSW.5 | User Flag              | General purpose flag                                  |
| RS1  | PSW.4 | Register Bank Select 1 | Used to select register bank                          |
| RS0  | PSW.3 | Register Bank Select 0 | Used to select register bank                          |
| OV   | PSW.2 | Overflow Flag          | Set when signed arithmetic overflow occurs            |
| —    | PSW.1 | Reserved               | Not used                                              |
| P    | PSW.0 | Parity Flag            | Set if accumulator has odd number of 1’s              |



## 12. How register bank is selected in 8051 microcontroller?

| RS1 | RS0 | Bank Selected | Address Range |
|-----|-----|--------------|---------------|
| 0   | 0   | Bank 0       | 00H – 07H     |
| 0   | 1   | Bank 1       | 08H – 0FH     |
| 1   | 0   | Bank 2       | 10H – 17H     |
| 1   | 1   | Bank 3       | 18H – 1FH     |



## 13. State the difference between RET and RETI instructions in 8051

| Feature        | RET                       | RETI                          |
|---------------|---------------------------|-------------------------------|
| Meaning       | Return from subroutine    | Return from interrupt         |
| Used in       | Normal subroutine         | Interrupt Service Routine     |
| Interrupt flag| Not affected              | Clears interrupt-in-progress flag |
| Stack usage   | Pops return address       | Pops return address           |



## 14. Differentiate microprocessor and microcontroller

| Feature          | Microprocessor             | Microcontroller                    |
|------------------|---------------------------|-----------------------------------|
| Components       | Only CPU                  | CPU + RAM + ROM + I/O + Timers    |
| Cost             | High                      | Low                               |
| Size             | Large                     | Compact                           |
| Applications     | General purpose systems   | Embedded systems                  |
| Power consumption| More                      | Less                              |



## 15. Compare polling and interrupts

| Polling                          | Interrupt                |
|----------------------------------|--------------------------|
| CPU continuously checks device   | Device notifies CPU      |
| Wastes CPU time                  | Efficient CPU usage      |
| Slower response                  | Faster response          |
| Simple to implement              | Slightly complex         |



## 16. Write an 8051 embedded C program to toggle port P1.0

```c
#include <reg51.h>

void delay();

sbit LED = P1^0;

void main()
{
    while(1)
    {
        LED = 1;
        delay();
        LED = 0;
        delay();
    }
}

void delay()
{
    unsigned int i, j;
    for(i = 0; i < 500; i++)
        for(j = 0; j < 1275; j++);
}
```



## 17. Compare compiler and cross compiler

| Compiler | Cross Compiler |
|----------|----------------|
| Runs and generates code for same machine | Runs on one machine, generates code for another |
| Example: GCC for PC | Example: Keil C for 8051 |
| Used in desktop development | Used in embedded systems |



## 18. Mention the role of scheduling in multitasking environment

Scheduling:

- Decides which task runs next  
- Allocates CPU time  
- Improves system efficiency  
- Maintains fairness  
- Ensures real-time constraints  

Types:

- Preemptive scheduling  
- Cooperative scheduling  



## 19. Define Context switching

Context switching is:

The process of saving the state (registers, PC, stack, etc.) of a currently running task and restoring the state of another task so that execution can resume.

It is essential in multitasking systems.



## 20. Write 8051 program to perform XOR operation

```asm
MOV A, #25H      ; Load first number
MOV R0, #35H     ; Load second number
XRL A, R0        ; A = A XOR R0
MOV 40H, A       ; Store result at RAM location 40H
END
```

If A = 25H and R0 = 35H  
Result = 10H
