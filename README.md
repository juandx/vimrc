我平时用python+vim编辑居多 所以在网上参考并使用了一些vim插件、主题、用法 希望能够分享出来并建立一个自己的vimrc

安装最新的vim  https://www.linuxprobe.com/vim8-0-linux.html
注意必须编译的时候加入允许python插入，不然后面youcompleteme的时候会报错 requires Vim compiled with Python (2.7 or 3.4+) support.
```
yum install ncurses-devel
wget https://github.com/vim/vim/archive/master.zip
unzip master.zip
cd vim-master
cd src/
./configure --enable-pythoninterp=yes
make
sudo make install
vim
```

1 首先是安装vendle， git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

2 然后替换这个vimrc,如果是mac直接在用户目录建立一个.vimrc文件

3 注意看到set rtp+=~/.vim/bundle/Vundle.vim ，把~换成自己的home目录，比如我的/home/wenbin/

4 Launch vim and run :PluginInstall 或者 To install from command line: vim +PluginInstall +qall

5 对youcompleteme 安装一对底层需要的编译的东西

  sudo yum install automake gcc gcc-c++ kernel-devel cmake python-devel

  cd ~/.vim/bundle/YouCompleteMe

  ./install.py --clang-completer

  ./install.py

6 下面是一些解释和用法

空格是代码折叠

F3是切换复制粘贴

F4是切换行号显示(行号使用相对+绝对行号) 

F5是格式化,把tab改为space，删除windows末尾^M

;fl 或者  :NERDTree 实现目录树，?是帮助，i是打开一个新的文件(类似:sp)

ctrl+p是查找文件，esc可以退出

molokai这个配色我很喜欢

:set nu, :set nonu 是切换行号出现和消失

先用v选择多行

ga进入easyalign模式 默认向左对其，比如按照空格对其 向右对其 居中对其 如果遇到其他字符比如 | , = 啥的，都把空格替换>为对应的即可 *可以换成数字，对应后面的第几个字符，就是全部都指定

:vsp file  或者  :vp file    是新窗口打开文件, 用 CTRL+w可以切换窗口

;gg   YCM 跳转到定义的函数

:open file  打开新的file文件后可以用   CTRL-^  或者  :e#  返回(:e#n 返回到n个之前的文件)

7 go 用法
  安装了vim-go 非常方便， gd是跳转到定义处，相当好用，其他请看https://github.com/fatih/vim-go
  但是，安装vim-go会有遇到几个问题，基本是包没装，而且有的包还在墙外面。。。大概要装下面几个
```
go get -u github.com/nsf/gocode
go get golang.org/x/tools/cmd/goimports
go get golang.org/x/tools/cmd/guru
go get golang.org/x/tools/cmd/gorename
```
