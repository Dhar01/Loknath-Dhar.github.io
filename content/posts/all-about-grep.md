---
title: "Let's learn: grep!"
date: 2022-12-13T11:30:03+06:00
showToc: true
TocOpen: false
draft: false
tags: ["tools", "linux", "cheatsheet"]
---

`grep`: Global Regular Expression print.

`grep` is a powerful program used to find text patterns within files. It uses **regular expressions** (*shortly regex*) to match the pattern.

When `grep` encounters a *pattern* in the file, it prints out the lines containing it. If no file is given, it will search recursively search the given pattern in the files in current directory.

```bash
grep pattern [file...]

grep <search-pattern> file.txt
```

- To show the line number in the output, use `-n` option:

```bash
grep -n <search-pattern> file.txt
```

> `grep` is case-sensitive.

- To ignore case-sensitive in grep, use `-i` option:

```bash
grep -i <search-pattern> file.txt
```

Use some special characters or regular expressions in grep:

- `^` : search at the beginning of the line.
- `$` : search at the end of the line.
- `.` : search any character.

Some handy options for grep:

- `-v` : tells `grep` to print only those lines that do not match the pattern.

# Variants

grep has two variants:

1. **egrep** : Extended grep.
2. **fgrep** : fast grep.

### Egrep

Egrep allows to use complicated regex.

For example, search any words that start with either `I` or `o`:

```bash
egrep '^(i/o)' file.txt
```

search any words starts in the range between `i` to `u`:

```bash
egrep '^[i-u]' file.txt
```