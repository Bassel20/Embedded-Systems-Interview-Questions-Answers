# RTOS Interview Questions & Answers for Embedded SW Engineers #

## Questions ##
* [Q1: What is a real time operating system?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q1-what-is-a-real-time-operating-system)
* [Q2: Tell me about RTOS task states](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q2-tell-me-about-rtos-task-states)
* [Q3: What is a kernel?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q3-what-is-a-kernel)
* [Q4: What is the difference between preemptive and non-preemptive kernel?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q4-what-is-the-difference-between-preemptive-and-non-preemptive-kernel)
* [Q5: Explain priority inheritance and inversion in real time operating systems](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q5-explain-priority-inheritance-and-inversion-in-real-time-operating-systems)
* [Q6: What are mutexes and semaphores?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Real%20Time%20Operating%20Systems%20(RTOS)%20Questions.md#q6-what-are-mutexes-and-semaphores)

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

## Q3: What is a kernel? ##

A kernel is the core component of the operating system that provides the foundation for managing system resources, such as the processor, memory, and I/O devices. The kernel is responsible for providing abstractions of hardware resources, managing access to those resources, and scheduling tasks to run on the processor.
The kernel typically provides services such as:

* **Task management:** The kernel manages tasks or threads that run concurrently in the system. It schedules and switches between tasks, manages task priorities, and provides mechanisms for synchronization and communication between tasks.
 
* **Memory management:** The kernel manages the allocation and deallocation of memory resources to tasks, including virtual memory management.

* **Device management:** The kernel manages access to I/O devices such as sensors, actuators, and communication interfaces. It provides mechanisms for interrupt handling and device driver management.
 
* **Time management:** The kernel provides mechanisms for measuring and managing time, including timers, clock sources, and scheduling policies.

* **Security:** The kernel provides mechanisms for controlling access to system resources and ensuring system security.

## Q4: What is the difference between preemptive and non-preemptive kernel? ##

**A preemptive kernel** allows higher-priority tasks to interrupt and pre-empt lower-priority tasks and switch to a higher priority task that is ready to run. 
preemptive kernels offer better responsiveness to real-time events and better utilization of system resources, but can have higher overhead and require more complex synchronization mechanisms.

**A non-preemptive kernel** does not allow the kernel to interrupt a running task. Instead, the running task must yield control to the kernel explicitly by making a system call or by blocking on a synchronization primitive. 
Non-preemptive kernels provide simpler scheduling algorithms, lower overhead, and more predictability than preemptive kernels. However, they can be less responsive to real-time events and less efficient in utilizing system resources.

## Q5: Explain priority inheritance and inversion in real time operating systems. ##

**Priority inversion** occurs when a high-priority task is blocked by a lower-priority task that is currently accessing a shared resource. For example, if a low-priority task acquires a lock on a shared resource, and then a high-priority task also needs to access the same resource, it will be blocked by the lower-priority task, causing priority inversion. This can cause serious problems in real-time systems, as it can lead to missed deadlines and incorrect behavior. 

**Priority inheritance** is a technique used to prevent priority inversion by temporarily raising the priority of the low-priority task to the level of the highest-priority task waiting for the shared resource.

In priority inheritance, when a high-priority task needs to access a shared resource that is currently being held by a lower-priority task, the low-priority task's priority is temporarily raised to the level of the high-priority task, allowing it to release the shared resource immediately. This ensures that the high-priority task can continue to execute without delay, preventing priority inversion.

Priority inheritance is typically implemented by the operating system or real-time kernel, and can be used in conjunction with other synchronization primitives, such as mutexes or semaphores, to prevent priority inversion.

## Q6: What are mutexes and semaphores? ##

Mutexes and semaphores are both synchronization mechanisms in RTOS used to control access to shared resources between different tasks or threads. Mutexes provide exclusive access to a resource, while semaphores allow for controlled access based on a count. Mutexes are primarily used for mutual exclusion, while semaphores have broader applications.

**Mutex**\
Mutex is a mutual exclusion object that synchronizes access to a resource. It is created with a unique name at the start of a program. The Mutex is a locking mechanism that makes sure only one thread can acquire the Mutex at a time and enter the critical section. This thread only releases the Mutex when it exits the critical section.

Example:
```
wait (mutex);
...
/* Critical Section */
...
signal (mutex);
```
A mutex is different than a semaphore as it is a locking mechanism while a semaphore is a signalling mechanism. A binary semaphore can be used as a Mutex but a Mutex can never be used as a semaphore.

**Semaphore**\
A semaphore is a signalling mechanism. A thread that is waiting on a semaphore can be signaled by another thread. This is different than a mutex as the mutex can be signaled only by the thread that called the wait function.

A semaphore uses two atomic operations, wait and signal for process synchronization.

The wait operation decrements the value of its argument S, if it is positive. If S is negative or zero, then no operation is performed.
```
wait(S)
{
   while (S<=0);
   S--;
}
```
The signal operation increments the value of its argument S.
```
signal(S)
{
   S++;
}
```
There are mainly two types of semaphores i.e. counting semaphores and binary semaphores.

Counting Semaphores are integer value semaphores and have an unrestricted value domain. These semaphores are used to coordinate the resource access, where the semaphore count is the number of available resources.

The binary semaphores are like counting semaphores but their value is restricted to 0 and 1. The wait operation only works when the semaphore is 1 and the signal operation succeeds when semaphore is 0.
