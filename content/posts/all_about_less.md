---
title: "Let's learn: less!"
date: 2022-11-13T11:30:03+06:00
showToc: true
TocOpen: false
draft: false
tags: ["tools", "linux", "cheatsheet"]
---

The `less` command is a program to view text files.

Example:

```bash
less filename

less /etc/passwd
```

Some action commands for `less`:
| Command | Action |
|---------|--------|
| `Page Up` or `b` | Scroll back one page |
| `Page Down` or `space` | Scroll forward one page |
| `Up Arrow` | Scroll up one line |
| `Down Arrow` | Scroll down one line |
| `G` | Move to the end of the text file |
| `g` or `1G` | Move to the beginning of the text file |
| `/characters` | search forward to the next occurrence of *characters* |
| `n` | search for the next occurrence of the previous search |
| `h` | display help screen |
| `q` | quit less |

> `less` is `more`
