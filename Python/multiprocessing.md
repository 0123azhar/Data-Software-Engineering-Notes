This module allows you to create and manage multiple processes.
A process is an independent ==program in execution== with its own memory space and resources. A process can have multiple threads.
Inter-process communication (IPC) mechanisms like pipes, queues, and shared memory are used to facilitate communication between processes.

`from multiprocessing import Process, Pool, Queue, current_process`