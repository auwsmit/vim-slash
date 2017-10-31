!FORK!
------

This is a fork of junegunn's vim-slash, but I removed the features involving
search highlighting.

* Why remove auto-clear search hl? Because I use [vim-cool](https://github.com/romainl/vim-cool)
for that.

* Why keep vim-slash like this at all? Because I like the improved star-search,
and I use `<plug>(slash-after)` with [vim-indexed-search](https://github.com/henrik/vim-indexed-search)
to show number of search results (e.g. 123 of 456):

```vim
" vim-slash + vim-indexed-search
Plug 'auwsmit/vim-slash' | Plug 'henrik/vim-indexed-search'
let g:indexed_search_mappings = 0
noremap <silent> <plug>(slash-after) :<c-u>ShowSearchIndex<cr>
xunmap <plug>(slash-after)
```

-----

vim-slash
=========

vim-slash provides a set of mappings for enhancing in-buffer search experience
in Vim.

- Automatically clears search highlight when cursor is moved
- Improved star-search (visual-mode, highlighting without moving)

Installation
------------

Using [vim-plug](https://github.com/junegunn/vim-plug):

```vim
Plug 'junegunn/vim-slash'
```

Comparison with vim-oblique
---------------------------

vim-slash is a smaller alternative to [vim-oblique][ob]. vim-oblique depends
on [a reimplementation of Vim command-line interface][pcl] which is incomplete
and has a number of issues that cannot be easily fixed. vim-oblique is also
much slower than the native /-search when working with large files.

Many features of vim-oblique are missing in vim-slash, but [frankly, my dear,
I don't give a damn][damn].

[ob]:   https://github.com/junegunn/vim-oblique
[pcl]:  https://github.com/junegunn/vim-pseudocl
[damn]: https://en.wikipedia.org/wiki/Frankly,_my_dear,_I_don%27t_give_a_damn

Customization
-------------

#### `zz` after search

Places the current match at the center of the window.

```vim
noremap <plug>(slash-after) zz
```

#### Blinking cursor after search using Vim 8 timer

```vim
if has('timers')
  " Blink 2 times with 50ms interval
  noremap <expr> <plug>(slash-after) slash#blink(2, 50)
endif
```

You can prepend `zz` to the expression: `'zz'.slash#blink(2, 50)`
