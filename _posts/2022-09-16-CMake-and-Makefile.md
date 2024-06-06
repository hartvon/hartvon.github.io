---
layout: post
title: "CMake and Makefile"
categories: Tools
toc: true
---

# CMake

# Makefile

> make是一个根据指定的 Shell 命令进行构建的工具。
>
> Makefile 规定要构建哪个文件、它依赖哪些源文件，当哪些文件有变动时，如何重新构建它


1. Rule

> 每条规则就明确两件事：
>
> - 构建目标的前置条件是什么
> - 如何构建

```Makefile
targets: prerequisites
    command
    command
    command
```

2. Variable

- Customed
  - `=`: Recursive expanded
  - `:=`: Simply expanded
- Predefined
- Automatic

3. Functions

- `$(patsubst pattern,replacement,text)` or

  `$(text:pattern=replacement)` or

  `$(text:suffix=replacement)`

- $(foreach var,list,text)

> https://makefiletutorial.com
