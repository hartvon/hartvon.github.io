---
layout: post
title: "Linux Commands"
categories: Tools
toc: true
---

## Shortcuts

- `ctrl + a/e`: Move to line begin/end.
- `ctrl + u/k`: Delete context before/behind cursor.

## Chaining Operators

- `&`: 同时在后台执行多个命令
- `;`: 顺序执行多个命令
- `&&`: 前一个命令执行成功时再执行后一个命令
- `||`: 前一个命令执行失败时再执行后一个命令
- `!`: 执行除了提供的条件外的所有的语句
- `&& ... ||`: 类似 *if...else* 语句
- `|`: 将第一个命令的输出作为第二个命令的输入
- `{}`: 合并两个或多个命令，第二个命令依赖于第一个命令的执行
- `()`: 让括号内的命令优先执行
- `\`: 将命令拆分成多行

## File Management

- `ll -h`: 'human', show file size in intuitive status.
- `cat / more / less / head / tail`
- `> / >>`: Redirect(Override / Append) output.
- `file/stat <file>`: Show file status.

## Find items

- `find <path> [-name/type/size/maxdepth/mindepth] <file>`
- `locate <file> [-i/n/r] <path>`
- `grep <content> [-r/i/n] <file>`
