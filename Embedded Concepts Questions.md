# Embedded concepts and common peripherals Interview Questions & Answers  #

## Questions ##
* [Q1: Explain types of memory in embedded systems in detail](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q1-explain-types-of-memory-in-embedded-systems-in-detail)
* [Q2: Explain how interrupts work in detail.](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q2-explain-how-interrupts-work-in-detail)
* [Q3: What is interrupt tail-chaining?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q3-what-is-interrupt-tail-chaining)
* [Q4: What is the difference between reentrant and non-reentrant functions?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q4-what-is-the-difference-between-reentrant-and-non-reentrant-functions)
* [Q5: What is the difference between synchronous and Asynchronous functions?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q5-what-is-the-difference-between-synchronous-and-asynchronous-functions)
* [Q6: How to measure the duty cycle of a signal with/without ICU (input capture unit)?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q6-how-to-measure-the-duty-cycle-of-a-signal-withwithout-icu-input-capture-unit)
* [Q7: Explain ADC in detail.](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q7-explain-adc-in-detail)
* [Q8: Explain Watchdog timer in detail.](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q8-explain-watchdog-timer-in-detail)
* [Q9: Tell me about PWM.](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q9-tell-me-about-pwm)
* [Q10: Explain how DMA works. What are some of the issues that you need to worry about when using DMA?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Embedded%20Concepts%20Questions.md#q10-explain-how-dma-works-what-are-some-of-the-issues-that-you-need-to-worry-about-when-using-dma)

----------------------------------------------------------------------------------------------------------------------------------------------------------------
## Questions & Answers: ##

### Q1: Explain types of memory in embedded systems in detail ###

Memory is mainly classified into **ROM**, **RAM**, and **Hybrid**.

**ROM (Read-Only Memory):** used to store the program code and data that is not meant to be modified during the system's operation. The data stored in ROM remains constant and can be accessed very quickly, making it ideal for storing frequently used data and program code.\
* **EPROM (Erasable Programmable Read-Only Memory):** can be programmed by applying a high voltage to the memory cell and can be erased using ultraviolet light.
*	**PROM (Programmable Read-Only Memory):** can be programmed using a device called a PROM programmer which blows fuses on the memory chip to set the memory cell to either a 0 or a 1. once programmed, the contents of PROM cannot be changed.
*	**Masked ROM:** manufactured with the desired program code or data pre-programmed into the memory chip during the manufacturing process. Once the memory chip is manufactured, the program code or data cannot be changed.

**RAM (Random Access Memory):** used for temporary storage of data and program instructions that change frequently during the system's operation. RAM is volatile, meaning that its contents are lost when the power is turned off or reset. RAM is divided into several segments:
*Stack memory:* Used for storing local variables, function calls, return addresses, etc.\
*Heap memory:* Used for dynamic memory allocation during runtime.\
*Static memory:* Used for storing global variables and static variables.\
*Data memory:* Used for storing data and constants.\
*Code memory:* Used for storing program code.

There are several types of RAM:
*	**SRAM (Static RAM):** uses latching circuitry to store data, which makes it faster and more power-efficient than other types of RAM. SRAM is typically used for storing small amounts of data that need to be accessed quickly, such as processor registers and cache memory.
*	**DRAM (Dynamic RAM):** This type of RAM uses a capacitor to store each bit of data, which requires refreshing the data periodically to maintain its integrity. DRAM is slower and less power-efficient than SRAM, but it is more cost-effective and can store larger amounts of data. DRAM is typically used for storing the main program code and data in embedded systems.
*	**SDRAM (Synchronous Dynamic RAM):** This type of RAM is a variant of DRAM that synchronizes the memory clock with the system clock, which allows for faster data access and more efficient use of the memory bus. SDRAM is typically used in high-performance embedded systems that require large amounts of memory and fast data access.
*	**DDR SDRAM (Double Data Rate Synchronous Dynamic RAM):** This type of RAM is an evolution of SDRAM that transfers data on both the rising and falling edges of the clock signal, which effectively doubles the data transfer rate. DDR SDRAM is typically used in high-performance embedded systems that require large amounts of memory and high-speed data access.

**Hybrid Memory**
*	**Flash Memory:** This type of memory is non-volatile and is used for storing the program code and data that can be modified during the system's operation. Flash memory is slower than RAM and ROM, but it can be reprogrammed multiple times, making it ideal for storing data that needs to be updated or modified frequently.
*	**EEPROM (Electrically Erasable Programmable Read-Only Memory):** This type of memory is non-volatile and is used for storing small amounts of data that need to be retained even when the power is turned off or reset. EEPROM can be reprogrammed multiple times, but it is slower than flash memory.
*	**NVRAM (Non-Volatile Random Access Memory):** can retain stored data even when power is removed. used to store critical system data that needs to be preserved across power cycles or system resets like configuration data, calibration data, security keys, and other critical system parameters. is preferred over other types of non-volatile memory like EEPROM or Flash memory as it offers faster read and write speeds and higher endurance. An example of NVRAM in embedded systems is the real-time clock (RTC) module, which is used to keep track of time and date even when power is off.
*	**Cache Memory:** This type of memory is used to improve the performance of the system by storing frequently accessed data and program instructions in a faster and more easily accessible memory location. Cache memory is typically built into the processor or the memory controller and can significantly reduce the access time to the main memory.

### Q2: Explain how interrupts work in detail. ###

Interrupts are events that require immediate attention. When an interrupt signal occurs, the normal program execution is temporarily suspended, and control is transferred to a specific Interrupt Service Routine (ISR) or interrupt handler. The ISR performs the necessary tasks to handle the interrupt, such as reading data from a peripheral or updating variables. Once the ISR completes, the interrupted program resumes its execution. Interrupts have priority levels, and higher-priority interrupts are serviced before lower-priority ones. Interrupts are managed by an interrupt controller and their addresses are stored in an interrupt vector table. Interrupts allow for efficient handling of time-critical events in embedded systems.

The interrupt process includes the following steps:
* The CPU executes the main program.
* An interrupt occurs and the CPU saves the current state of the program.
* The CPU jumps to the interrupt vector, which contains the address of the ISR.
* The ISR is executed.
* Once the ISR is finished, the CPU returns to the main program and resumes its execution from where it was interrupted.

### Q3: What is interrupt tail-chaining? ###

Interrupt tail-chaining is a technique used in some microcontrollers and processors to improve the efficiency of the interrupt handling process.

In tail-chaining, when a higher-priority interrupt occurs while the processor is servicing a lower-priority interrupt, instead of interrupting the current interrupt service routine (ISR) immediately, the processor allows the current ISR to complete and then begins executing the ISR for the higher-priority interrupt. This technique is called tail-chaining because the new interrupt is added to the end of the current ISR execution, like a chain.

By using tail-chaining, the processor can avoid the overhead of saving and restoring context when switching between ISRs. This saves time and reduces the latency of high-priority interrupts. Tail-chaining is most effective when there is a lot of processing overhead associated with saving and restoring context, or when there are many nested interrupts.

However, tail-chaining can also have some downsides. If the processor spends too much time servicing the current ISR, the higher-priority interrupt may be delayed significantly. Additionally, tail-chaining can make it more difficult to reason about interrupt handling, as the order of execution is not always straightforward.

### Q4: What is the difference between reentrant and non-reentrant functions? ###

**A reentrant API** can be safely called/interrupted by multiple threads or processes simultaneously without causing data integrity issues or unexpected behavior. This is achieved by not relying on shared state or global variables, instead using local variables or passing parameters between function calls. typically used in multi-threaded or multi-process applications, as they can be called safely by multiple threads without any additional synchronization or locking mechanisms.\
**A non-reentrant API** cannot be safely called by multiple threads or processes simultaneously without causing data integrity issues or unexpected behavior as it relies on shared state or global variables. may require additional synchronization mechanisms, such as locks or semaphores, to ensure thread safety.

### Q5: What is the difference between synchronous and Asynchronous functions? ###

**Synchronous** functions block the program until the function completes its task and returns a result. It is a blocking architecture, so the execution of each operation is dependent on the completion of the one before it. Each task requires an answer before moving on to the next iteration. This can be useful when you need the result immediately and don't need to do anything else until the result arrives.\
**Asynchronous** functions allow the program to continue executing other tasks while waiting for the function to complete its task. It is a non-blocking architecture, so the execution of one task isn’t dependent on another, and tasks can run simultaneously. This can be useful when you have multiple tasks to perform and don't want to block the program while waiting for the function to complete.

### Q6: How to measure the duty cycle of a signal with/without ICU (input capture unit)? ###

The duty cycle of a signal is a measure of the percentage of time that the signal is in its active state (i.e., high) over a given period. There are different methods for measuring the duty cycle of a signal with and without ICU (Input Capture Unit).

**Without ICU:**
We can use an oscilloscope or a digital multimeter with a frequency measurement feature by following these steps:
*	Connect the signal to the input of the measuring device.
*	Set the measuring device to frequency measurement mode.
*	Measure the frequency of the signal.
*	Measure the duration of one cycle of the signal.
*	Calculate duty cycle using this formula: Duty cycle = (pulse duration / cycle duration) x 100%.

**With ICU:**
We can measure the duty cycle of a signal using the input capture feature of the microcontroller by following these steps:
*	Configure the microcontroller's ICU module to capture the rising edge of the signal.
*	Start the timer module of the microcontroller.
*	Wait for the signal to change from high to low.
*	Capture the timer value at the falling edge of the signal.
*	Calculate the pulse duration using the captured timer values.
*	Calculate duty cycle using this formula: Duty cycle = (pulse duration / total time) x 100%.

### Q7: Explain ADC in detail. ###
ADC (Analog to Digital Converter) is an important peripheral used in embedded systems to convert analog signals to digital signals. Here is how ADC works in detail:

*	**Sampling:** The first step of the convertion process is to take a sample of the analog signal at a specific time interval. This is done using a sampling circuit that holds the input signal at a constant value for a specific period.

*	**Quantization:** In this step, the sampled analog signal is converted into a digital signal. The analog signal is divided into a specific number of levels, and each level is assigned a specific digital value. The resolution of an ADC is determined by the number of levels that can be assigned.

*	**Encoding:** After quantization, the digital value of the analog signal is encoded into a binary number, using the ADC's internal circuits. The encoding process varies depending on the type of ADC used.

*	**Conversion:** Once the analog signal is converted to a digital signal, it is stored in a register. The ADC then transfers the data to the microcontroller or processor, where it can be further processed.

*	**Scaling and Calibration:** The final step of ADC is to scale and calibrate the digital signal. Scaling involves mapping the digital values to the actual values of the input signal. Calibration is done to correct any errors in the conversion process and to ensure accurate results.

### Q8: Explain Watchdog timer in detail. ###
A watchdog timer is a countdown timer which is used to reset a microprocessor after a specific interval of time. It is a safety mechanism that can detect if the device has stopped functioning due to a software bug, hardware failure or other reasons, and take corrective actions.

It works by continuously monitoring the system and generating a reset signal if it detects that the system has stopped functioning or has become unresponsive. This reset signal will cause the microcontroller or the device to restart and resume normal operation.

The watchdog timer consists of a free-running timer that is periodically reloaded with a value. If the timer is not reloaded within a specific time period, it generates a reset signal to the microcontroller or the device. The time period is usually set by a software configuration register and can range from a few microseconds to several seconds. This time period is determined/calculated according to the longest path of tasks possible by the system (worst case scenario).

The watchdog timer is used to improve the reliability and safety of embedded systems by providing a mechanism to automatically recover from software or hardware failures.

There are certain failures that cannot be corrected by a reset, for example the watchdog timer cannot prevent or detect the corruption of data memory. Unless corruption of data affects program flow, or some extra measures are taken (self-diagnostic sw), data corruption will not cause a watchdog timeout.

Examples of software/hardware failures that cause the watchdog timer to reset the system:
*	**Stack overflow or underflow:** If the software stack used by the microcontroller overflows or underflows, it can cause the program to crash or enter an infinite loop, leading to system failure.
*	**Deadlock or infinite loop:** If the software enters a deadlock or infinite loop, it can cause the system to become unresponsive, leading to system failure.
*	**Interrupt storm:** If the microcontroller receives a high number of interrupts in a short period of time, it can cause the system to become unresponsive, leading to system failure.
*	**Power supply fluctuations:** If there are fluctuations in the power supply voltage, it can cause the microcontroller to malfunction or become unresponsive, leading to system failure.

### Q9: Tell me about PWM. ###

Pulse width modulation is a digital technique for controlling analog circuits using microprocessor’s digital outputs. PWM is used in a wide variety of applications including measurement, communications, power control, and conversion. It is mostly used in embedded systems for controlling the speed of motors, dimming LEDs, generating analog signals, and controlling the power delivered to other devices.

In PWM, a square wave signal is used, where the duty cycle (the percentage of time the signal is on) determines the average voltage or current delivered to a device. The average voltage or current is proportional to the duty cycle, so by varying the duty cycle, the amount of power delivered to a device can be controlled.

In a microcontroller, PWM is implemented using a timer/counter module that is dedicated to generating PWM signals. The timer/counter module is configured to generate a PWM signal with a specific frequency and duty cycle.

Here are the steps involved in using PWM in a microcontroller:
*	**Configure the timer/counter** to generate a PWM signal with the desired frequency and duty cycle. This involves setting the clock source, the prescaler, and the mode of operation for the timer/counter.
*	**Set the duty cycle** of the PWM signal by writing a value to a register that controls the PWM output.
*	**Enable the PWM output** by setting a bit in a register that controls the PWM output pin.
*	**Update the duty cycle:** The duty cycle can be updated at any time by writing a new value to the register that controls the PWM output.
*	**Use the PWM signal:** Once the PWM output is enabled, the PWM signal can be used to control the power delivered to a device, such as a motor or an LED.

### Q10: Explain how DMA works. What are some of the issues that you need to worry about when using DMA? ###

DMA (Direct Memory Access). It is a feature that allows data to be moved between peripherals and memory without the need for the CPU to be involved. Instead of the CPU managing the data transfer, the DMA controller manages the data transfer.

The basic operation of DMA involves three main components:\
**DMA controller:** responsible for managing the data transfer between the peripheral and memory.\
**Peripheral:** sends a request to the DMA controller to initiate a data transfer.\
**Memory:** DMA controller then reads or writes data to or from the memory based on the request from the peripheral.

Some of the issues that need to be considered when using DMA include:
*	**DMA channel allocation:** There are typically a limited number of DMA channels available in a system. Careful consideration is required to allocate DMA channels to various peripherals to avoid conflicts and ensure efficient data transfer.
*	**Memory allocation:** The DMA controller needs to access memory to read or write data. Memory needs to be allocated appropriately to ensure that the DMA controller does not interfere with other parts of the system.
*	**Data consistency:** When using DMA, there is a possibility that the CPU and DMA controller may access the same memory location at the same time, resulting in data consistency issues. This can be resolved by using memory protection mechanisms and ensuring that the CPU and DMA controller do not access the same memory location at the same time.
*	**Interrupts:** DMA controllers can generate interrupts when data transfer is complete. Interrupts need to be handled appropriately to ensure that data is processed in a timely and efficient manner.
*	**Power consumption:** DMA can be power-hungry, so power management mechanisms need to be in place to ensure that power consumption is optimized. This is especially important in battery-powered systems.
