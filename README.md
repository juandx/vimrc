
```
如果vim意外关闭，一般会保留一个.filename.swp文件，你vim filename 的时候会提示你，一般键入r进行继续编辑上次没改完的内容，或者键入e编辑上次修改之前的内容，然后保存退出，然后再vim filename，键入d删除.filename.swp就行
```

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
make install
vim
```

1 首先是安装vendle， git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

2 然后替换这个vimrc,如果是mac直接在用户目录建立一个.vimrc文件

3 注意看到set rtp+=~/.vim/bundle/Vundle.vim ，把~换成自己的home目录，比如我的/home/wenbin/

4 Launch vim and run :PluginInstall 或者 To install from command line: vim +PluginInstall +qall

5 对youcompleteme 安装一对底层需要的编译的东西

  yum install automake gcc gcc-c++ kernel-devel cmake python-devel

  cd ~/.vim/bundle/YouCompleteMe

  ./install.py --clang-completer

  ./install.py

6 下面是一些解释和用法

空格是代码折叠

F3是切换复制粘贴

F4是切换行号显示(行号使用相对+绝对行号) 

F5是格式化,把tab改为space，删除windows末尾^M


F8 和 F9 是vimgrep搜索的下一个和上一个结果

F10是缓冲区显示

F11是缓冲区下一个文件

F12是缓冲区上一个文件

;fl 或者  :NERDTree 实现目录树，?是帮助，i是打开一个新的文件(类似:sp)

ctrl+p是查找文件，esc可以退出

单词自动补全：
CTRL+n ：当你输入第一个字母的时候，再CTRL+n，自动出现下拉菜单，单词默认选中第一个，继续CTRL+n，CTRL+p可以上下切换，或者用方向键（太慢）

CTRL+p ：同上，只是默认的选中的是列表中最后一个单词

molokai这个配色我很喜欢

:set nu, :set nonu 是切换行号出现和消失 同F4

先用v选择多行

ga进入easyalign模式 默认向左对其，比如按照空格对其 向右对其 居中对其 如果遇到其他字符比如 | , = 啥的，都把空格替换>为对应的即可 *可以换成数字，对应后面的第几个字符，就是全部都指定

:vsp file  或者  :vp file    是新窗口打开文件, 用 CTRL+w可以切换窗口

;gg   YCM 跳转到定义的函数

:open file  打开新的file文件后可以用   CTRL-^  或者  :e#  返回(:e#n 返回到n个之前的文件)

:cw  打开vimgrep搜索结果
:ccl 关闭vimgrep搜索结果

```

vim[grep] 命令行：
:vim[grep] /pattern/[g][j] files ...


g 选项：
不加该选项时，当一行中有多个匹配项时，仅在 quickfix 中添加一行。添加该选项时，每个匹配都在 quickfix 列表中添加一项。

j 选项：
不加该选项，查找完毕，光标将跳转到第一个匹配处。添加该选项时，查找完毕，仅更新 quickfix 列表，光标不跳转。


:vim /wenbin/g pkg/**/* *.go
表示 比如当前目录(kubernetes)下有pkg文件下，想搜索pkg文件夹下所有.go文件中含有字符串wenbin的文件
       :cw打开搜索列表  :ccl关闭搜索列表    F8 和 F9 是下一个上一个结果
```
7 go 用法
  安装了vim-go 非常方便， gd是跳转到定义处，相当好用，其他请看https://github.com/fatih/vim-go
  但是，安装vim-go会有遇到几个问题，基本是包没装，而且有的包还在墙外面。。。大概要装下面几个
```
go get -u github.com/nsf/gocode
go get golang.org/x/tools/cmd/goimports
go get golang.org/x/tools/cmd/guru
go get golang.org/x/tools/cmd/gorename
```
