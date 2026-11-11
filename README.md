# OS Laboratory Activity 3
## Multilevel Queue and Real-Time CPU Scheduling
 
### Student Information
- Name: LONGCOB, SHERIE Q.
- Course and Section: BSCA - B186.1
- Instructor: PROF BAHINTING, MARIA FE P. 
- Date Submitted:11/12/2026
 
### I. Introduction
This laboratory activity focuses on the implementation and simulation of three CPU scheduling algorithms: Multilevel Queue (MLQ), Rate Monotonic Scheduling (RMS), and Earliest Deadline First (EDF) using Python.

The activity aims to demonstrate how different scheduling algorithms manage processes and tasks depending on their priorities, execution times, and deadlines. Through these implementations, we can observe how the CPU allocates its processing time, how processes are executed, and how real-time tasks meet or miss their deadlines.

Each program generates a Gantt chart to visualize the execution sequence and provides relevant scheduling results. These include waiting time, turnaround time, CPU utilization, and deadline compliance.

This activity also provides practical experience in Python programming, algorithm analysis, and using GitHub for source code management and project documentation.
 
### II. Objectives
The main objectives of this laboratory activity are:

    To understand the operation and differences between Multilevel Queue, Rate Monotonic Scheduling, and Earliest Deadline First algorithms.

    o implement Multilevel Queue scheduling using Round Robin and First Come, First Served (FCFS). 

    To develop preemptive Rate Monotonic Scheduling and Earliest Deadline First simulations using Python.

    To generate and interpret Gantt charts representing process and task execution.

    To calculate CPU utilization, waiting time, turnaround time, and determine whether real-time tasks meet their deadlines.

    To create and manage a GitHub repository containing the Python source codes, program outputs, and laboratory documentation.
 
### III. Scheduling Algorithms
1. Multilevel Queue Scheduling
        Multilevel Queue Scheduling divides processes into separate queues based on their categories and priorities. In this implementation, there are two queues with different scheduling policies.

Queue 1 – Round Robin (RR): Handles interactive processes using a time quantum of 2 milliseconds. Each process receives CPU time based on the assigned quantum.

Queue 2 – First Come, First Served (FCFS): Handles batch processes and executes them according to their arrival order.

Queue 1 has strict priority over Queue 2. When a Queue 1 process becomes available, it can interrupt a currently running Queue 2 process. The interrupted process resumes once Queue 1 has no more processes waiting.

2. Rate Monotonic Scheduling
        Rate Monotonic Scheduling is a fixed-priority preemptive scheduling algorithm designed for periodic real-time tasks. It assigns priorities according to the task periods: the shorter the period, the higher the priority. In this implementation, T1 receives the highest priority because it has the shortest period, followed by T2 and T3. The program simulates task execution over 20 milliseconds and generates a Gantt chart to show how the CPU schedules each task. It also calculates CPU utilization and checks the task set against the RMS sufficient utilization bound.

3. Earliest Deadline First
        Earliest Deadline First is a dynamic-priority preemptive scheduling algorithm that selects the ready task with the earliest absolute deadline. Unlike RMS, which uses fixed priorities based on task periods, EDF determines priority based on the deadlines of available task instances. A newly released task with an earlier deadline can take priority over the currently running task. The program simulates periodic task execution over 20 milliseconds, generates a Gantt chart, calculates CPU utilization, and determines whether each task instance meets or misses its deadline.
 
### IV. Program Implementation
The laboratory activity was implemented using Python 3. Each scheduling algorithm was developed in a separate Python file to keep the programs organized and easier to understand.

1. Multilevel Queue Scheduling – mlq.py

        The MLQ program uses Python's deque from the collections module to manage the two process queues. Processes are assigned to Queue 1 or Queue 2 based on their queue number. Round Robin is applied to Queue 1 with a time quantum of 2 milliseconds, while Queue 2 follows FCFS scheduling. The program also handles preemption when a higher-priority Queue 1 process becomes available. After simulating the execution, it generates a Gantt chart and calculates the completion time, turnaround time, and waiting time of each process. It also displays the average turnaround time and average waiting time.

2. Rate Monotonic Scheduling – rms.py

        The RMS program uses a fixed-priority scheduling approach. Task priorities are arranged according to their periods, giving higher priority to tasks with shorter periods. The program generates periodic task instances, each with its own release time, execution time, and deadline. It then simulates CPU execution using 1-millisecond intervals and selects the highest-priority ready task. After the simulation, the program generates a Gantt chart, calculates CPU utilization, determines the RMS sufficient utilization bound, and checks the deadline status of each task instance.

3. Earliest Deadline First – edf.py

        The EDF program implements dynamic-priority preemptive scheduling. It generates periodic task instances and selects the ready task with the earliest absolute deadline. During each 1-millisecond interval, the program checks the available tasks and selects the one with the earliest deadline. If two tasks have the same deadline, the earlier release time and task ID are used as tie-breakers. After execution, the program generates a Gantt chart, calculates CPU utilization, evaluates the classical EDF utilization test, and identifies task instances that meet or miss their deadlines.
                Simulation Assumptions

                        All three programs follow the laboratory activity's specified simulation settings:

                        Each simulation uses a 1-millisecond time interval.

                        Context-switching overhead is ignored.

                        RMS and EDF use a simulation duration of 20 milliseconds.

                        Each periodic task instance is treated as a separate job with its own release time, remaining execution time, and deadline.
 
### V. Test Data
The following test data were used for the three scheduling algorithms:

1. Multilevel Queue Scheduling (MLQ)

        The program uses five processes:

                P1: Arrival Time = 0, Burst Time = 5, Queue = 1
                P2: Arrival Time = 1, Burst Time = 4, Queue = 1
                P3: Arrival Time = 0, Burst Time = 6, Queue = 2
                P4: Arrival Time = 2, Burst Time = 3, Queue = 2
                P5: Arrival Time = 3, Burst Time = 2, Queue = 1

        Queue 1 uses Round Robin with a time quantum of 2 ms, while Queue 2 uses FCFS.

2. Rate Monotonic Scheduling (RMS)

        The program uses three periodic tasks:

                T1: Execution Time = 1 ms, Period = 4 ms, Deadline = 4 ms
                T2: Execution Time = 1 ms, Period = 5 ms, Deadline = 5 ms
                T3: Execution Time = 2 ms, Period = 10 ms, Deadline = 10 ms

        Simulation Duration: 20 ms

3. Earliest Deadline First (EDF)

        The program uses the same three periodic tasks as RMS:

                T1: Execution Time = 1 ms, Period = 4 ms, Deadline = 4 ms
                T2: Execution Time = 1 ms, Period = 5 ms, Deadline = 5 ms
                T3: Execution Time = 2 ms, Period = 10 ms, Deadline = 10 ms
                Simulation Duration: 20 ms

        All simulations use a 1 ms time interval, and context-switching overhead is ignored.