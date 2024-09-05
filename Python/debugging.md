breakpoint()
When the interpreter hits a breakpoint in your code, it will stop.

press:

n to step to the next line in the current function. If the code calls functions, it will execute them but the debugger does not get into them.

s to step to the next line in the current function. If the next
line is a function, the debugger goes into that, and you can then run one
instruction of that function at a time

c to continue the execution of the program normally, without the need to do it step-by-step.

q to stop the execution of the program.