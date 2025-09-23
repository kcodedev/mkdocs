# Process Management

## Understanding Process Management

A process is an instance of a program in execution. Each process gets its own space in the computer's memory, so they don't interfere with each other. Process management is a core function of an operating system (OS) responsible for overseeing the execution of programs. It involves creating, scheduling, and terminating processes to ensure efficient use of system resources like CPU time, memory, and I/O devices. Effective process management enables multitasking, where multiple programs appear to run simultaneously on a single processor.

## Multi-tasking and Processes

### Multi-tasking
Multi-tasking is the ability of an OS to execute multiple tasks concurrently. This is achieved through time-sharing, where the CPU rapidly switches between processes, giving the illusion of parallelism. Multi-tasking improves system responsiveness and resource utilization, allowing users to run applications like web browsers, text editors, and background services at the same time.

## Process States

Processes transition through various states during their lifecycle:

- **Running**: The process is currently executing on the CPU.
- **Ready**: The process is prepared to run but is waiting for CPU time.
- **Blocked/Waiting**: The process is waiting for an event or resource, such as I/O completion or user input.

These states are managed by the OS scheduler, which moves processes between states based on system events and resource availability.

## Scheduling

### The Need for Scheduling
Scheduling is essential because system resources are limited. The CPU scheduler allocates processor time to processes, ensuring fair access and optimal performance. Without scheduling, processes might monopolize resources, leading to starvation or poor responsiveness.

### Scheduling Algorithms

Different algorithms balance factors like fairness, efficiency, and response time:

- **First Come First Served (FCFS)**: Processes are executed in the order they arrive. Simple but can lead to long wait times for short processes (convoy effect).
- **Shortest Job First (SJF)**: Prioritizes processes with the shortest expected execution time. Minimizes average waiting time but requires knowledge of process duration.
- **Shortest Remaining Time (SRT)**: A preemptive version of SJF that switches to shorter processes as they arrive. Reduces waiting time but increases context switching overhead.
- **Round Robin (RR)**: Each process gets a fixed time slice (quantum) before being preempted. Promotes fairness and responsiveness, especially for interactive systems, but may increase overhead from frequent switches.

## First Come First Served (FCFS)

### Example Processes

| Process | Duration | Arrival Time |
|---------|----------|--------------|
| P1      | 5        | 0            |
| P2      | 3        | 1            |
| P3      | 1        | 2            |

### CPU Timeline

<table>
<tr><th>Process</th><td colspan="5">P1</td><td colspan="3">P2</td><td colspan="1">P3</td></tr>
<tr><th>Time</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td></tr>
</table>

## Shortest Job First (SJF)

### Example Processes

| Process | Duration | Arrival Time |
|---------|----------|--------------|
| P1      | 5        | 0            |
| P2      | 3        | 1            |
| P3      | 1        | 2            |

### CPU Timeline

<table>
<tr><th>Process</th><td colspan="5">P1</td><td colspan="1">P3</td><td colspan="3">P2</td></tr>
<tr><th>Time</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td></tr>
</table>

## Shortest Remaining Time (SRT)

### Example Processes

| Process | Duration | Arrival Time |
|---------|----------|--------------|
| P1      | 5        | 0            |
| P2      | 3        | 1            |
| P3      | 1        | 2            |

### CPU Timeline

<table>
<tr><th>Process</th><td colspan="1">P1</td><td colspan="3">P2</td><td colspan="1">P3</td><td colspan="4">P1</td></tr>
<tr><th>Time</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td></tr>
</table>

## Round Robin (RR)

### Example Processes

| Process | Duration | Arrival Time |
|---------|----------|--------------|
| P1      | 5        | 0            |
| P2      | 3        | 1            |
| P3      | 1        | 2            |

*Quantum: 2 time units*

### CPU Timeline

<table>
<tr><th>Process</th><td colspan="2">P1</td><td colspan="2">P2</td><td colspan="1">P3</td><td colspan="2">P1</td><td colspan="1">P2</td><td colspan="1">P1</td></tr>
<tr><th>Time</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td></tr>
</table>

## Kernel and Interrupt Handling

The OS kernel acts as the interrupt handler, managing hardware interrupts that signal events like I/O completion or timer expiration. When an interrupt occurs:

1. The current process's state is saved.
2. The kernel's interrupt service routine (ISR) executes to handle the event.
3. Control may return to the interrupted process or switch to another via the scheduler.

Interrupt handling enables low-level scheduling by allowing the kernel to preempt processes, update timers, and manage resource allocation dynamically. This ensures timely responses to external events and maintains system stability in multi-tasking environments.