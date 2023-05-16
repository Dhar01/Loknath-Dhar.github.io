---
title: "Most common Vim/Neovim Settings"
date: 2023-03-15
draft: false
---

As I edit system configuration files day to day basis, my number one choice for text editor is vim. So here's a post about some common settings:

```vim
" Number-related settings
set number               " Display line numbers
set relativenumber       " Display relative line numbers
set signcolumn=yes       " Always show the sign column

" Search-related settings
set hlsearch             " Highlight search results
set incsearch            " Highlight search matches as you type
set ignorecase           " Ignore case when searching
set smartcase            " Ignore case only if search pattern is all lowercase

" Appearance-related settings
set laststatus=2         " Always show status line
set cursorline           " Highlight current line
" set colorcolumn=80       " Display a vertical line at column 80 to help with line length
set noerrorbells         " Disable error bells and visual bells
set wrap                 " Wrap long lines visually
set linebreak            " Break long lines at word boundaries

" Window-related settings
set splitright           " Split windows to the right
set splitbelow           " Split windows below
set scrolloff=5          " Keep 5 lines above/below cursor when scrolling
set clipboard+=unnamed   " Copy text to system clipboard
set mouse=a              " Enable mouse support

" Completion-related settings
set wildmenu             " Show command-line completion options in a menu
set wildmode=list:longest,full  " Highlight and complete the longest common part of the options

" Mode-related settings set showmode             " Show current mode (insert/visual/command) in status line

" Folding-related settings
set foldmethod=indent    " Use indent-based folding
set foldlevelstart=99    " Start with all folds open

" Wrapping-related settings
set whichwrap+=<,>,h     " Allow wrapping past the beginning or end of a line


" Create a horizontal split with Ctrl+s
nnoremap <C-s> :split<CR>
" Create a vertical split with Ctrl+v
nnoremap <C-v> :vsplit<CR>
" Create a new horizontal split and start editing a new file with Ctrl+n
nnoremap <C-n> :split<CR>:enew<CR>
" Create a new vertical split and start editing a new file with Ctrl+m
nnoremap <C-m> :vsplit<CR>:enew<CR>
```

Thanks!
