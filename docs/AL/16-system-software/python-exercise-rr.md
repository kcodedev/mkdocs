# Round Robin Scheduling Simulator Problem 🐍

**Task:**  
Write a Python program to simulate Round Robin (RR) scheduling for a set of processes.

Your program should:

1. Take input for a list of processes (each with an ID, arrival time, and burst time) and a time quantum.
2. Simulate the Round Robin scheduling algorithm.
3. Output the execution timeline (showing which process runs at each time unit) and the average waiting time for the processes.

This exercise demonstrates process scheduling, multi-tasking, and time-sharing concepts from operating system process management.

---

## Step-by-Step Guidance

### Step 1 — Represent processes
- Use a list of dictionaries for processes, each with keys: 'id', 'arrival', 'burst', 'remaining_burst' (initially equal to burst), 'completion_time'.

### Step 2 — Set up the simulation
- Use a queue (from collections import deque) to hold ready processes.
- Initialize current_time = 0, timeline = [] (list to record process at each time unit).
- Sort processes by arrival time initially.

### Step 3 — Simulate scheduling
- While there are unfinished processes (remaining_burst > 0):
  - Add all processes that have arrived (arrival <= current_time) to the ready queue, if not already there.
  - If ready queue is not empty:
    - Dequeue the next process.
    - Determine run_time = min(quantum, process['remaining_burst']).
    - For each time unit in run_time, append process['id'] to timeline, increment current_time.
    - Decrement process['remaining_burst'] by run_time.
    - If remaining_burst > 0, enqueue the process back.
    - Else, set process['completion_time'] = current_time.
  - Else, increment current_time (idle time, but assume no idle in examples).

### Step 4 — Calculate waiting times
- For each process, waiting_time = completion_time - arrival - burst.
- Compute average waiting time = sum(waiting_times) / number of processes.

### Step 5 — Output results
- Print the timeline as a string or list.
- Print the average waiting time.

---

**Example to test:**  
Processes:  
- P1: arrival=0, burst=5  
- P2: arrival=1, burst=3  
- P3: arrival=2, burst=1  

Quantum: 2  

Timeline: ['P1', 'P1', 'P2', 'P2', 'P3', 'P1', 'P1', 'P2', 'P1']  

Completion times: P1=9, P2=8, P3=5  
Waiting times: P1=9-0-5=4, P2=8-1-3=4, P3=5-2-1=2  
Average waiting time: (4+4+2)/3 ≈ 3.33