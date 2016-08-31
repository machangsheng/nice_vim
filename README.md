# nice_vim
make it easy

##1. 从安装源编译vim
1. 安装必要库：
> `sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev 
    libgtk2.0-dev libatk1.0-dev libbonoboui2-dev 
    libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev 
    python3-dev ruby-dev lua5.1 lua5.1-dev git`

2. 卸载残留：
> `sudo apt-get remove vim vim-runtime gvim vim-tiny vim-common vim-gui-common vim-nox`

3.  源码安装：  

> `cd ~`   

>`git clone https://github.com/vim/vim.git`    

>`cd vim`   

>`./configure --with-features=huge --enable-multibyte --enable-rubyinterp --enable-pythoninterp --with-python-config-dir=/usr/lib/python2.7/config --enable-python3interp --with-python3-config-dir=/usr/lib/python3.5/config --enable-perlinterp --enable-luainterp --enable-gui=gtk2 --enable-cscope --prefix=/usr`   

>`make VIMRUNTIMEDIR=/usr/share/vim/vim74`   

>`sudo make install``

##2. 安装vundle   
1. 介绍:

   安装需要[Git](http://git-scm.com/),触发[`git clone`](http://gitref.org/creating/#clone),默认将每一个指定特定格式插件的仓库复制到`~/.vim/bundle/`.
   搜索需要Curl支持.

   Windows用户请直接访问[Windows setup]. 如果有任何问题, 请参考 [FAQ].
   查看 [Tips] 获取相关高级配置.

   使用 non-POSIX shells, 比如比较流行对 Fish shell, 需要额外对步骤. 请查看 [FAQ].

2. 初始安装 [Vundle]:

   `$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

3. 配置插件 :

   请将以下加在 `.vimrc` 方可使用Vundle. 删掉你不需要的插件, 这些只是用做示例.

   ```vim
   set nocompatible              " 去除VI一致性,必须
   filetype off                  " 必须

   " 设置包括vundle和初始化相关的runtime path
   set rtp+=~/.vim/bundle/Vundle.vim
   call vundle#begin()
   " 另一种选择, 指定一个vundle安装插件的路径
   "call vundle#begin('~/some/path/here')

   " 让vundle管理插件版本,必须
   Plugin 'VundleVim/Vundle.vim'

   " 以下范例用来支持不同格式的插件安装.
   " 请将安装插件的命令放在vundle#begin和vundle#end之间.
   " Github上的插件
   " 格式为 Plugin '用户名/插件仓库名'
   Plugin 'tpope/vim-fugitive'
   " 来自 http://vim-scripts.org/vim/scripts.html 的插件
   " Plugin '插件名称' 实际上是 Plugin 'vim-scripts/插件仓库名' 只是此处的用户名可以省略
   Plugin 'L9'
   " 由Git支持但不再github上的插件仓库 Plugin 'git clone 后面的地址'
   Plugin 'git://git.wincent.com/command-t.git'
   " 本地的Git仓库(例如自己的插件) Plugin 'file:///+本地插件仓库绝对路径'
   Plugin 'file:///home/gmarik/path/to/plugin'
   " 插件在仓库的子目录中.
   " 正确指定路径用以设置runtimepath. 以下范例插件在sparkup/vim目录下
   Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
   " 安装L9，如果已经安装过这个插件，可利用以下格式避免命名冲突
   Plugin 'ascenator/L9', {'name': 'newL9'}

   " 你的所有插件需要在下面这行之前
   call vundle#end()            " 必须
   filetype plugin indent on    " 必须 加载vim自带和插件相应的语法和文件类型相关脚本
   " 忽视插件改变缩进,可以使用以下替代:
   "filetype plugin on
   "
   " 简要帮助文档
   " :PluginList       - 列出所有已配置的插件
   " :PluginInstall    - 安装插件,追加 `!` 用以更新或使用 :PluginUpdate
   " :PluginSearch foo - 搜索 foo ; 追加 `!` 清除本地缓存
   " :PluginClean      - 清除未使用插件,需要确认; 追加 `!` 自动批准移除未使用插件
   "
   " 查阅 :h vundle 获取更多细节和wiki以及FAQ
   " 将你自己对非插件片段放在这行之后
   ```

4. 安装插件:

   运行 `vim` 再运行 `:PluginInstall`

   通过命令行直接安装 `vim +PluginInstall +qall`

