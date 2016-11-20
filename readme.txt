Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-11-09T00:26:36+08:00

====== vimrc ======
Created 星期三 09 十一月 2016
**My Vim Setting**
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
{{~/Pictures/2016-11-10 15-34-11 的屏幕截图.png}}
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 定义快捷键的前缀,即 <Leader>
let mapleader=";"
set t_Co=256

nmap gh 0
nmap gl $
"设置快捷键将文本复制到系统剪贴板
vnoremap <Leader>y "+y
"设置快捷键将系统剪贴板复制到vim
vnoremap <Leader>p "+p

" 定义快捷键保存当前窗口内容
nmap <Leader>w :w<CR>
" 定义快捷键保存所有窗口内容并退出
nmap <Leader>WQ :wa<CR>:q<CR>
" 不做任何保存,直接退出 vim
nmap <Leader>Q :qa!<CR>
" 依次遍历子窗口
nnoremap nw <C-W><C-W>
" 跳转至右方窗口
nnoremap <Leader>lw <C-W>l
" 跳转至左方窗口
nnoremap <Leader>hw <C-W>h
" 跳转至上方窗口
nnoremap <Leader>kw <C-W>k
" 跳转至左方窗口
nnoremap <Leader>jw <C-W>j

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 文件类型侦测

" 开启文件类型侦测
filetype on
" 根据侦测到的不同类型加载对应的插件
filetype plugin on

" <<

" 让配置变更立即生效
autocmd BufWritePost $MYVIMRC source $MYVIMRC

" 其他

" 开启实时搜索功能vundle
set incsearch

" 搜索时大小写不敏感
set ignorecase

" 关闭兼容模式
set nocompatible

" vim 自身命令行模式智能补全
set wildmenu " << 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 配色方案

"set background=dark
"colorscheme solarized
colorscheme molokai
"colorscheme phd

" 营造专注气氛

"  禁止光标闪烁
"set gcr=a:block-blinkon0

"  禁止显示滚动条
set guioptions-=l
set guioptions-=L
set guioptions-=r
set guioptions-=R

"  禁止显示菜单和工具条
"set guioptions-=m
"set guioptions-=T

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 辅助信息

" 总是显示状态栏
set laststatus=2

" 显示光标当前位置
set ruler

" 开启行号显示
set number

" 高亮显示当前行/列
set cursorline
set cursorcolumn

" 高亮显示搜索结果
set hlsearch

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 其他美化

" 设置 gvim 显示字体
set guifont=YaHei\ Consolas\ Hybrid\ 16

" 禁止折行
set nowrap

" 设置状态栏主题风格
let g:Powerline_colovundlerscheme='solarized256'

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 语法分析

" 开启语法高亮功能
syntax enable
" 允许用指定语法高亮配色方案替换默认方案
syntax on

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
""""""""""""""""""""" Vundle
set nocompatible
"filetype off

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'gmarik/vundle'
Plugin 'Valloric/YouCompleteMe'
Plugin 'Valloric/ListToggle'
Plugin 'scrooloose/syntastic'
Plugin 'SirVer/ultisnips'
Plugin 'honza/vim-snippets'
Plugin 'ervandew/supertab'
Plugin 'lokaltog/vim-powerline'
Plugin 'majutsushi/tagbar'
Plugin 'vim-scripts/indexer.tar.gz'
Plugin 'vim-scripts/DfrankUtil'
Plugin 'vim-scripts/vimprj'
Plugin 'scrooloose/nerdcommenter'
Plugin 'scrooloose/nerdtree'
Plugin 'jistr/vim-nerdtree-tabs'
Plugin 'fholgado/minibufexpl.vim'
Plugin 'lilydjwg/fcitx.vim'
Plugin 'lokaltog/vim-easymotion'

call vundle#end()
filetype plugin indent on
"安装   :PluginInstall
"卸载   :PluginClean
"更新   :PluginUpdate
""""""""""""""""vundle""""" Vundle

"map <leader><space> :FixWhitespace<cr>	" \+space去掉末尾空格

" <<

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 缩进

" 自适应不同语言的智能缩进
filetype indent on

" 将制表符扩展为空格
"set expandtab

" 缩进可视化插件 Indent Guides
" 随 vim 自启动
let g:indent_guides_enable_on_vim_startup=1
" 从第二层开始可视化显示缩进
let g:indent_guides_start_level=2
" 色块宽度
let g:indent_guides_guide_size=1
" 快捷键 i 开/关缩进可视化
nmap <silent> <Leader>i <Plug>IndentGuidesToggle

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 标签列表

" 启动时自动focus
"let g:tagbar_autofocus=1
" 如果是C/C++,自动运行
autocmd BufReadPost *.cpp,*.c,*.h,*.hpp,*.cc,*.cxx call tagbar#autoopen()
" 如果是Python,自动运行
autocmd BufReadPost *.py,*.sh call tagbar#autoopen()
"autocmd VimEnter * wincmd p
set tags=tags;
set autochdir
let g:tagbar_ctags_bin='ctags'
" 设置 tagbar 子窗口的位置出现在主编辑区的左边
let tagbar_right=1
" 设置显示／隐藏标签列表子窗口的快捷键。速记：identifier list by tag
nnoremap <Leader>ilt :TagbarToggle<CR>
" 设置标签子窗口的宽度
let tagbar_width=26
" tagbar 子窗口中不显示冗余帮助信息
let g:tagbar_compact=1
" 设置 ctags 对哪些代码标识符生成标签
let g:tagbar_type_cpp = {
	 \ 'ctagstype' : 'c++',
	 \ 'kinds'     : [
		 \ 'c:classes:0:1',
		 \ 'd:macros:0:1',
		 \ 'e:enumerators:0:0', 
		 \ 'f:functions:0:1',
		 \ 'g:enumeration:0:1',
		 \ 'l:local:0:1',
		 \ 'm:members:0:1',
		 \ 'n:namespaces:0:1',
		 \ 'p:functions_prototypes:0:1',
		 \ 's:structs:0:1',
		 \ 't:typedefs:0:1',
		 \ 'u:unions:0:1',
		 \ 'v:global:0:1',
		 \ 'x:external:0:1'
	 \ ],
	 \ 'sro'        : '::',
	 \ 'kind2scope' : {
		 \ 'g' : 'enum',
		 \ 'n' : 'namespace',
		 \ 'c' : 'class',
		 \ 's' : 'struct',
		 \ 'u' : 'union'
	 \ },
	 \ 'scope2kind' : {
		 \ 'enum'      : 'g',
		 \ 'namespace' : 'n',
		 \ 'class'     : 'c',
		 \ 'struct'    : 's',
		 \ 'union'     : 'u'
	 \ }
\ }

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 代码折叠

" 基于缩进或语法进行代码折叠
"set foldmethod=indent
set foldmethod=syntax
" 启动 vim 时关闭折叠代码
set nofoldenable
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 代码导航
 
" 基于标签的代码导航

" 设置插件 indexer 调用 ctags 的参数
" 默认 --c++-kinds=+p+l，重新设置为 --c++-kinds=+l+p+x+c+d+e+f+g+m+n+s+t+u+v
" 默认 --fields=+iaS 不满足 YCM 要求，需改为 --fields=+iaSl
let g:indexer_ctagsCommandLineOptions="--c++-kinds=+l+p+x+c+d+e+f+g+m+n+s+t+u+v --fields=+iaSl --extra=+q"

" 正向遍历同名标签
nmap <Leader>tn :tnext<CR>
" 反向遍历同名标签
nmap <Leader>tp :tprevious<CR>

" 基于语义的代码导航

nnoremap <leader>jc :YcmCompleter GoToDeclaration<CR>
" 只能是 #include 或已打开的文件
nnoremap <leader>jd :YcmCompleter GoToDefinition<CR>

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 工程文件浏览

autocmd VimEnter * NERDTree
autocmd VimEnter * wincmd p
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTreeType") &&b:NERDTreeType == "primary") | q | endif

let NERDTreeShowBookmarks=1
"let g:nerdtree_tabs_open_on_console_startup=1
" 使用 NERDTree 插件查看工程文件。设置快捷键，速记：file list
nmap <Leader>fl :NERDTreeToggle<CR>
" 设置 NERDTree 子窗口宽度
let NERDTreeWinSize=26
" 设置 NERDTree 子窗口位置
let NERDTreeWinPos="left"
" 显示隐藏文件
let NERDTreeShowHidden=0
" NERDTree 子窗口中不显示冗余帮助信息
let NERDTreeMinimalUI=1
" 删除文件时自动删除文件对应 buffer
let NERDTreeAutoDeleteBuffer=1

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 多文档编辑
set hidden 
"let g:miniBufExplMapCTabSwitchBufs=1
let g:miniBufExplMapCTabSwitchBufs = 1
" 显示/隐藏 MiniBufExplorer 窗口
map <Leader>bl :MBEToggle<cr>

" buffer 切换快捷键
map <Leader><TAB> :MBEbn<cr>
map <Leader><S-TAB> :MBEbp<cr>
"noremap <C-TAB>   :MBEbf<CR>
"noremap <C-S-TAB> :MBEbb<CR>
" <<

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
set autoindent       	 " 设置自动对齐(缩进)：即每行的缩进值与上一行相等
set smartindent        	 " 智能对齐方式
set cul			 " 显示当前行下划线
set tabstop=4 		 " 设置制表符(tab键)的宽度
set softtabstop=4     	 " 设置软制表符的宽度    
set shiftwidth=4        " (自动) 缩进使用的4个空格
set cindent              " 使用 C/C++ 语言的自动缩进方式
set cinoptions={0,1s,t0,n-2,p2s,(03s,=.5s,>1s,=1s,:1s     " 设置C/C++语言的具体缩进方式
set backspace=2          " 设置退格键可用
set mouse=a              " 使用鼠标
set number        
set completeopt=longest,menu	"让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)
autocmd InsertLeave * if pumvisible() == 0|pclose|endif	"离开插入模式后自动关闭预览窗口
inoremap <expr> <CR>       pumvisible() ? "\<C-y>" : "\<CR>"	
"回车即选中当前项
"上下左右键的行为 会显示其他信息
inoremap <expr> <Down>     pumvisible() ? "\<C-n>" : "\<Down>"
inoremap <expr> <Up>       pumvisible() ? "\<C-p>" : "\<Up>"
inoremap <expr> <PageDown> pumvisible() ? "\<PageDown>\<C-p>\<C-n>" : "\<PageDown>"
inoremap <expr> <PageUp>   pumvisible() ? "\<PageUp>\<C-p>\<C-n>" : "\<PageUp>"

" <<

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" easymotion-快速跳转
let g:EasyMotion_smartcase=1

" <Leader>f{char} to move to {char}
map  <Leader>f <Plug>(easymotion-bd-f)
nmap <Leader>f <Plug>(easymotion-overwin-f)
" s{char}{char} to move {char}{char}
nmap s <Plug>(easymotion-overwin-f2)
" Move to line
map  <Leader>L <Plug>(easymotion-bd-jk)
nmap <Leader>L <Plug>(easymotion-overwin-line)
" Move to word
map  <Leader>w <Plug>(easymotion-bd-w)
nmap <Leader>w <Plug>(easymotion-overwin-w)
map <Leader><Leader>h <Plug>(easymotion-linebackward)
map <Leader><Leader>j <Plug>(easymotion-j)
map <Leader><Leader>k <Plug>(easymotion-k)
map <Leader><Leader>l <Plug>(easymotion-lineforward)
" 重复上次操作,强大
map <Leader><Leader>. <Plug>(easymotion-repeat)
" <<

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" >>
" YouCompleteMe
 
"Do not ask when starting vim
let g:ycm_confirm_extra_conf = 0
let g:syntastic_always_populate_loc_list = 1
set completeopt=longest,menu	"让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)
autocmd InsertLeave * if pumvisible() == 0|pclose|endif	"离开插入模式后自动关闭预览窗口
"回车即选中当前项
inoremap <expr> <CR>       pumvisible() ? "\<C-y>" : "\<CR>" 
"上下左右键的行为 会显示其他信息
inoremap <expr> <Down>     pumvisible() ? "\<C-n>" : "\<Down>"
inoremap <expr> <Up>       pumvisible() ? "\<C-p>" : "\<Up>"
inoremap <expr> <PageDown> pumvisible() ? "\<PageDown>\<C-p>\<C-n>" : "\<PageDown>"
inoremap <expr> <PageUp>   pumvisible() ? "\<PageUp>\<C-p>\<C-n>" : "\<PageUp>"

let g:ycm_collect_identifiers_from_tags_files=1	" 开启 YCM 基于标签引擎
let g:ycm_min_num_of_chletars_for_completion=2	" 从第2个键入字符就开始罗列匹配项
let g:ycm_cache_omnifunc=0	" 禁止缓存匹配项,每次都重新生成匹配项
let g:ycm_seed_identifiers_with_syntax=1	" 语法关键字补全

" make YCM compatible with UltiSnips (using supertab)
let g:ycm_key_list_select_completion = ['<C-n>', '<Down>']
let g:ycm_key_list_previous_completion = ['<C-p>', '<Up>']
let g:SuperTabDefaultCompletionType = '<C-n>'

" better key bindings for UltiSnipsExpandTrigger
let g:UltiSnipsExpandTrigger = "<tab>"
let g:UltiSnipsJumpForwardTrigger = "<tab>"
let g:UltiSnipsJumpBackwardTrigger = "<s-tab>"

"force recomile with syntastic
nnoremap <F5> :YcmForceCompileAndDiagnostics<CR>
nnoremap <leader>lo :lopen<CR>	"open locationlist
nnoremap <leader>lc :lclose<CR>	"close locationlist
inoremap <leader><leader> <C-x><C-o>

"在注释输入中也能补全
let g:ycm_complete_in_comments = 1
"在字符串输入中也能补全
let g:ycm_complete_in_strings = 1
"注释和字符串中的文字也会被收入补全
let g:ycm_collect_identifiers_from_comments_and_strings = 0

"跳转到定义处
nnoremap <leader>jd :YcmCompleter GoToDefinitionElseDeclaration<CR> 

"filetype plugin indent on 	" 打开文件类型检测
"set completeopt=longest,menu	" 关掉智能补全时的预览窗口
"set cscopequickfix=s-,c-,d-,i-,t-,e-

" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" >>
" 定义函数AutoSetFileHead，自动插入文件头
function! AutoSetShFileHead()
	"如果文件类型为.sh文件
	if &filetype == 'sh'
		so ~/config/sh_header.vim
		exe "1,6g/File Name :.*/s//File Name : " .expand("%:t")
		exe "1,6g/Creation Date :.*/s//Creation Date : " .strftime("%Y-%m-%d %H:%M")
	endif

	normal G
	normal o
	normal o
endfunc

function! AutoSetPyFileHead()
	"如果文件类型为python
	if &filetype == 'python'
		so ~/config/py_header.vim
		exe "1,6g/File Name :.*/s//File Name : " .expand("%:t")
		exe "1,6g/Creation Date :.*/s//Creation Date : " .strftime("%Y-%m-%d %H:%M")
	endif

	normal G
	normal o
	normal o
endfunc

function! AutoSetCFileHead()
	if &filetype == 'h' || &filetype == "cpp" || &filetype == "c"
		"如果文件类型为.cpp文件
		if &filetype == 'cpp'
			so ~/config/cpp_header.vim
		endif
		if &filetype == 'c' 
			so ~/config/c_header.vim
		endif
		exe "1,6g/File Name :.*/s//File Name : " .expand("%:t")
		exe "1,6g/Creation Date :.*/s//Creation Date : " .strftime("%Y-%m-%d %H:%M")
       
		"如果文件类型为.h文件
		if &filetype == 'h'
			exe "1,9g/^#include.*/s//#pragma once/"
		endif
	endif

	normal G
	normal o
	normal o
endfunc

autocmd BufNewFile *.sh exec ":call AutoSetShFileHead()"
autocmd BufNewFile *.py exec ":call AutoSetPyFileHead()"
autocmd BufNewFile *.c,*.cpp,*.h exec ":call AutoSetCFileHead()"

function! AutoChangeModifiedTime()
	execute "normal ma"
	exe "1,6g/Last Modified :.*/s/Last Modified :.*/Last Modified : " .strftime("%Y-%m-%d %H:%M")
	execute "normal `a"
	execute "normal ma"
endfunc

autocmd BufWritePre,FileWritePre,FileAppendPre *.c,*.h,*.cpp,*.py execute ":call AutoChangeModifiedTime()"
" <<
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
