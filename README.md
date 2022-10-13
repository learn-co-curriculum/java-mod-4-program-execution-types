# Program Execution Types

## Learning Goals

- Define sequential, concurrent, and parallel types of program execution.

## Introduction

Program Instructions are executed by the CPU. Instructions can be run in
different orders. If a program performs multiple tasks, sometimes it can be
programmed to run these tasks at the same time instead of completing them one by
one. This comes with various tradeoffs that we’ll discuss in later lessons.

## Synchronous Execution

If programs are run completely synchronously by a system, each task is scheduled
one at a time on the CPU. Every single task must be run to completion before any
other task can be scheduled.

For example, assume we have two tasks and each task requires 5 instructions
to be executed in order to complete the task.
We will represent an instruction as a dash `-` in the timeline shown below.

Synchronous execution requires task#1 to complete all 5 instructions
before task#2 can begin. 

```text
task#1  - - - - -
task#2            - - - - -

time    1 2 3 4 5 6 7 8 9 10 
```

## Concurrent Execution

A program is concurrent if it can be broken down into multiple tasks which can be
executed in interleaving order without changing the result.
Concurrent systems can either run multiple distinct programs or multiple tasks
of the same program in overlapping time intervals.

Although concurrent programs can have multiple tasks in progress at the same
time, the CPU doesn’t execute instructions of the various tasks at the same
time. Their execution is interleaved which means each task is given some time on
the CPU before being switched out for another task.

The timeline below shows a possible interleaving of the tasks.
Task#1 executes 2 instructions before its execution is
temporarily suspended, at which point task#2 is allowed to 
execute 3 instructions.
The tasks take turns executing their instructions,
with only one task running at a given point in time.

```text
task#1  - -       -     - -
task#2      - - -   - -

time    1 2 3 4 5 6 7 8 9 10 
```

As an example, a web browser that runs on a system with a single core is
concurrent. The browser has to be able to process user input while still
rendering content on screen. If the user performs an action such as clicking
the mouse while content is being loaded, the loading task
will be paused to acknowledge and process the user’s action.

## Parallel Execution

Parallel execution allows a system to run multiple programs or tasks at the same
time unlike in concurrent execution where one task has to be suspended in order
to process another. Note that a program does have to be concurrent, i.e., parts
of the program has to be able to run independently without changing the final
result in order to run the program in parallel.

```text
task#1  - - - - -
task#2  - - - - -

time    1 2 3 4 5 6 7 8 9 10 
```

Almost all modern computers and mobile devices have CPUs with multiple cores
which means each core can process different programs or tasks at the same time.
Chances are that there are multiple programs running on the device you’re
currently reading this on!

## Summary

We’ve learned that concurrency is a method of handling multiple programs or
tasks by scheduling them in a certain way and parallelism is a way to run
multiple tasks simultaneously.
