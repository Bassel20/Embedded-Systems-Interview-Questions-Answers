# RTOS Interview Questions & Answers for Embedded SW Engineers #

## Questions ##
* [Q1: What is a real time operating system?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q1-what-is-a-real-time-operating-system)
* [Q2: Tell me about RTOS task states](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q2-tell-me-about-rtos-task-states)


----------------------------------------------------------------------------------------------------------------------------------------------------------------
## Questions & Answers: ##

### Q1: What is a real time operating system? ###

A Real Time Operating System is an operating system that is optimised for use in embedded/real time applications. Their primary objective is to ensure a timely and deterministic response to events. An event can be external, like a limit switch being hit, or internal like a character being received.
Using a real time operating system allows a software application to be written as a set of independent tasks. Each task is assigned a priority and it is the responsibility of the Real Time Operating System to ensure that the task with the highest priority that is able to run is the task that is running. Examples of when a task may not be able to run include when a task is waiting for an external event to occur, or when a task is waiting for a fixed time period

### Q2: Tell me about RTOS task states ###

A task can exist in one of the following states:

**Running**\
When a task is executing. It is currently utilising the processor. If the processor on which the RTOS is running only has a single core then there can only be one task in the Running state at any given time.

**Ready**\
Ready tasks are able to execute (they are not in the Blocked or Suspended state) but are not currently executing because a different task of equal or higher priority is already in the Running state.

**Blocked**\
The task is waiting for either a temporal or external event. For example, if a task calls vTaskDelay() it will block (be placed into the Blocked state) until the delay period has expired - a temporal event. Tasks can also block to wait for queue, semaphore, event group, notification or semaphore event. Tasks in the Blocked state normally have a 'timeout' period, after which the task will be timeout, and be unblocked, even if the event the task was waiting for has not occurred.
Tasks in the Blocked state do not use any processing time and cannot be selected to enter the Running state.

**Suspended**\
Like tasks that are in the Blocked state, tasks in the Suspended state cannot be selected to enter the Running state, but tasks in the Suspended state do not have a time out. Instead, tasks only enter or exit the Suspended state when explicitly commanded to do so through the vTaskSuspend() and xTaskResume() API calls respectively.

![Alt_text](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Figures/RTOS_task_states.gif)
