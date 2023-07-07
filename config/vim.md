# VIM

```vim
// Some code
" UI Base
set nocompatible " behave Vi-compatible as much as possible
set syntax=on " syntax to be loaded for current buffer
set autoindent " take indent for new line from previous line
set tabstop=4 " number of spaces that <Tab> in file uses
set softtabstop=4 " number of spaces that <Tab> uses while editing
set shiftwidth=4 " number of spaces to use for (auto)indent step
set number " print the line number in front of each line
set encoding=utf-8 " encoding used internally
set ignorecase " ignore case in search patterns
set smartcase "no ignore case when pattern has uppercase o
set hlsearch " highlight matches with last search pattern
set incsearch " highlight match while typing search pattern
set gdefault " the ':substitute' flag 'g' is default on
set langmenu=zh_CN.UTF-8 " language to be used for the menus
set termencoding=utf-8 " character encoding used by the terminal
set helplang=cn " preferred help languages
set ruler " show cursor line and column in the status line
set showmatch " briefly jump to matching bracket if insert one
set matchtime=5 " tenths of a second to show matching paren
set matchpairs=(:),{:},[:],<:> " pairs of characters that '%' can match
set novisualbell " use visual bell instead of beeping o
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936 " automatically detected character encodings
set t_co=256
filetype on " switch file type detection on/off
filetype plugin indent on
" let setting
let mapleader = ","
" nerdtree
let NERDTreeShowHikden=1
let NERDTreeShowLineNumbers=1
let NERDTreeAutoCenter=1
let NERDTreeIgnore=['\.pyc','\~$','\.swp']
let NERDTreeShowBookmarks=1
let g:NERDTreeDirArrowExpandable = '▸'
let g:NERDTreeDirArrowCollapsible = '▾'
let g:neocomplcache_enable_at_startup = 1
let g:neocomplcache_enable_auto_select = 1
let g:airline_powerline_fonts = 1
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#buffer_nr_show = 1
" airline
let g:airline#extensions#tabline#buffer_idx_mode = 1
" ctrlp
let g:ctrlp_custom_ignore = '\v[\/]\.(git|zip|rar)$'
" map setting
map <C-L> :NERDTreeToggle<CR>
nmap <leader>1 <Plug>AirlineSelectTab1
nmap <leader>2 <Plug>AirlineSelectTab2
nmap <leader>3 <Plug>AirlineSelectTab3
nmap <leader>4 <Plug>AirlineSelectTab4
nmap <leader>5 <Plug>AirlineSelectTab5
nmap <leader>6 <Plug>AirlineSelectTab6
nmap <leader>7 <Plug>AirlineSelectTab7
nmap <leader>8 <Plug>AirlineSelectTab8
nmap <leader>9 <Plug>AirlineSelectTab9
nmap <leader>- <Plug>AirlineSelectPrevTab
nmap <leader>= <Plug>AirlineSelectNextTab
autocmd FileType python,shell,coffee set commentstring=#\ %s
autocmd FileType java,c,cpp set commentstring=//\ %s
```
