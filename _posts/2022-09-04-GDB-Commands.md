---
layout: post
title: "GDB Commands"
categories: Tools
toc: true
---

GDB is command line utility

> Good practice: Use command `gdb` with `-tui` flag, it will show a gui interface.

- `r/run`: Start running program until a breakpoint or end of program
- `start`: Start running program until the begining of "main" function
- `b/break fun`: Set a breakpoint at the begining of function "fun"
- `b N`: Set a breakpoint at line number N of source file currently executing
- `b file.c:N`: Set a breakpoint at line number N of file "file.c"
- `d/delete N`: Remove breakpoint number N
- `disable`
- `i/info b/break`: List all breakpoints
- `c/continue`: Continues/Resumes running the program until the next breakpoint or end of program
- `f/finish`: Runs until the current function is finished
- `s/step`: Runs the next line of the program
- `s N`: Runs the next N lines of program
- `n/next`: Like s, but it does not step into functions
- `p/print var`: Prints the current value of the variable "var"
- `display, undisplay`: 
- `set var=val`: Assign "val" value to the variable "var"
- `bt`: Prints a stack trace
- `q/quit`: Quit from gdb