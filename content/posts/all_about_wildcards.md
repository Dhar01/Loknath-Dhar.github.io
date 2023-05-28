---
title: "Let's learn: Wildcards!"
date: 2023-01-18T11:30:03+06:00
showToc: true
TocOpen: false
draft: false
tags: ["tools", "linux", "cheatsheet"]
---


Wildcards (*also known as globbing*) allows us to select filenames based on patterns of characters.

| Wildcard | Meaning |
|----------|---------|
| `*` | matches any character |
| `?` | matches any single character |
| `[characters]` | matches any *character* that is a member of the *set characters* |
| `[!characters]` | matches any *character* that is <ins>not</ins> a member of the *set characters* |
| `[[:class:]]` | matches any *character* that is a member of the specified *class* |

Commonly used *character classes*:
| Character class | meaning |
|-----------------|---------|
| `[:alnum:]` | matches any alphanumeric character |
| `[:alpha:]` | matches any alphabetic character |
| `[:digit:]` | matches any numeral |
| `[:lower:]` | matches any lowercase letter |
| `[:upper:]` | matches any UPPERCASE letter |

#### Examples

`[[:upper:]]*` : Any file beginning with an uppercase letter.

`*[[:lower:]123]` : Any file ending with a lowercase letter or
the numerals “1”, “2”, or “3”.

`BACKUP.[0-9][0-9][0-9]` : Any file beginning with “BACKUP.”
followed by exactly three numerals.

`[abc]*` : Any file beginning with either an “a”, a
“b”, or a “c”
