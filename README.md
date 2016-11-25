# vimrc
wenbin's vimrc,  good for python

我平时用python+vim编辑居多
所以在网上参考并使用了一些vim插件、主题、用法
希望能够分享出来并建立一个自己的vimrc

1 首先是安装vendle，
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

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

:NERDTree 实现目录树，?是帮助，i是打开一个新的文件(类似:sp)

ctrl+p是查找文件，esc可以退出

molokai这个配色我很喜欢

:nu,  :nonu 是切换行号出现和消失

先用v选择多行

ga进入easyalign模式
默认向左对其，比如按照空格对其  *<space>
向右对其 <enter>*<space>
居中对其 <enter><enter>*<space>
如果遇到其他字符比如 | , = 啥的，都把空格替换为对应的即可
*可以换成数字，对应后面的第几个字符，*就是全部都指定

F4是切换行号显示(行号使用相对+绝对行号)
F5是格式化,把tab改为space，删除windows末尾^M
