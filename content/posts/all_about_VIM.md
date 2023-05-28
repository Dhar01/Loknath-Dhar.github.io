---
title: "Let's learn: Vim/NeoVim!"
date: 2023-02-08T11:30:03+06:00
showToc: true
TocOpen: false
draft: false
tags: ["tools", "linux", "cheatsheet"]
---

Syntax: `vim filename`.

# Movement

#### Navigating

- `h` /`j`/`k`/`l` :
- `C-U`/`C-D` : half-page up/down.
- `C-B`/`C-F` : page up/down.

- `H` : move to top of the screen.
- `M` : move to middle of the screen.
- `L` : move to bottom of the screen.

#### Words

- `b`/`w` : previous/next word.
- `ge`/`e` : previous/next end of word.

- `gj` : move cursor down (*multi-line text*).
- `gk` : move cursor up (*multi-line text*).

#### Line

- `$` : to the end of the line (*including last character*).
- `0` : move to the start of the line.
- `^` : start of line (*after white-space*).
- `G` : Last line.
- `gg` : First line.
- `:n` : Go to line *n*.
- `nG` : Go to line *n*.

- `Ctrl+o` : go back to where we came from.
- `Ctrl+i` : repeat to go back.

~ OTHERS

- `gj` : move cursor down (*multi-line text*).
- `gk` : move cursor up (*multi-line text*).

# Editing

### Exciting

- `q!` : quit editor without saving changes.
- `wq` : write & quit.
- `q` : quit (*normal*).

- `Esc`/`Ctrl+[`: exit insert mode.
- `i` :  Insert (*before the cursor*).
- `a` : append.
- `A` : append from end of line.
- `o` : next line.
- `O` : previous line.
- `s` : delete char and insert.
- `S` : delete line and insert.
- `C` : delete until end of line and insert.
- `r` : replace one character.
- `R` : enter replace mode.
- `u` undo changes.
- `Ctrl+R` : redo changes.

### Clipboard

- `x` : delete word under the cursor.
- `dw` : delete a word.
- `d$` : delete to the end of the line.
- `dd` : delete a whole line.
- `yy` : copy a line.
- `p` : paste.
- `P` : paste before.

- `U` : fix a whole line.

- `r` : change character.
- `ce` : change until the end of a word.
- `c$` : change until the end of the line.

- `Ctrl+g` : show file location and status.
- `%` : move to the matching parenthesis/bracket. (*debugging help*)

# Operators list

- `d` : delete.
- `y` : yank.
- `c` : change (*delete than insert*).
- `>` : indent right.
- `<` : indent left.
- `=` : auto-indent.
- `g~` : swap case.
- `gU` : UPPERCASE.
- `gu` : lowercase

# Pattern

`/pattern` : search for the pattern on forward direction.

- n : for forward searching
- N : for backward searching

`?pattern` : search for backward direction.

Place the cursor under the word (*Normal mode*)
`*` OR `G` WILL HIGHLIGHT THAT WORD

- `s/old/new/g` : Substitute *new* for all *old* on a line type (*globally*).
- `%s/old/new/g` : substitute all occurrences in the file type.
- `:%s/old/new/gc` : find every occurrence in the whole file, with a prompt whether to substitute or not.
- `:%s//replace/g` - Substitute last search by *replace* in the current file.


> Take a look at [vim settings](https://dhar01.github.io/posts/common-vim-neovim-settings/)