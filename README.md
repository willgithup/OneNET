the book is so greate about vim ide config.

for me; something diffirent about the env.
1   ubuntu + xshell + and the color scheme for xshell is solarized.

2    diffrent things with the book
     set background=dark but
     colorscheme solarized  substitute with the  desert.
     
     set cursorline
     set cursorcolumn  are both added the "hi CursorLine cterm=NONE ctermbg=black ctermfg=green guibg=NONE guifg=NONE";
     
     let g:indent_guides_auto_colors = 0                                          
     autocmd VimEnter,Colorscheme * :hi IndentGuidesOdd  guibg=green ctermbg=black                                 
     autocmd VimEnter,Colorscheme * :hi IndentGuidesEven guibg=NONE ctermbg=black  are added for indent bar;
     
     YCM install:
     http://blog.csdn.net/karlkei/article/details/72583306    this baby is ok!
     record the important steps;
 
 二：安装vim补全插件YouCompleteMe


准备工作：
1. 首先查看vim对于python的支持：vim --version |grep pthon
将对python3的支持切换成python2的支持
安装py2包：sudo apt-get install vim-nox-py2
切换支持的命令：sudo update-alternatives --config vim
手动切换py2和py3
2. 安装官方哪个文档上说的CMake和python3-dev
sudo apt-get install build-essential cmake
sudo apt-get install python-dev python3-dev
3. 安装YCM安装需要的Clang
sudo apt-get instal Clang


正式安装：
首先，我们要明确一点，这是个写程序时相当好用的插件，但是它超！级！大！
一般情况下直接通过vundle添加路径安装，但是vim界面并没有进度条，而且推出后又要重头开始！
这对耐心是极大的考验……


所以有另外一个方法,建议直接下载在~/.vim/bundle/下


1.git clone http://github.com/Valloric/YouCompleteMe.git ~/.vim/bundle/YouCompleteMe
2.cd ~/.vim/bundle/YouCompleteMe
3. git submodule update--init--recursive


下载完成后，添加Plugin 'Valloric/YouCompleteMe' ，保存后在vim界面执行:PluginInstall就能瞬间完成了：）
下载完成后，可以选择YCM支持的语言：
像是需要添加C语言支持的
1.cd ~/.vim/bundle/YouCompleteMe
2../install.py --clang-completer --system-libclang


如果都有需要，保证xbuild,go,tsserver,node,npm,cargo等工具包均安装完成后
1.cd ~/.vim/bundle/YouCompleteMe
2../insta;;/py --all


YVM配置
官方文档中有：
YCM looks for a .ycm_extra_conf.py file in the directory of the opened file or in any directory above it in the hierarchy (recursively); when the file is found, it is loaded (only once!) as a Python module. 
在~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/下可以找到.ycm_extra_conf.py这个文件，可以每次使用时把其复制到当前目录下，也可以在~/.vimrc中进行配置。


1 let g:ycm_global_ycm_extra_conf = ‘~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py’       "配置全局路径
2 let g:ycm_confirm_extra_conf=0   "每次直接加载该文件，不提示是否要加载


同时要补全语言，要对.ycm_extra_conf.py进行修改：
在flags下添加在flags下添加


1 ‘-isystem‘,
2 ‘/usr/include‘,
3 ‘-isystem‘,
4 ‘usr/include/c++/5.4.0‘
5 ‘-isystem‘,
6 ‘usr/include/x86_64-linux-gnu/c++‘,


并注释掉这一段：


1 try:
2      final_flags.remove( ‘-stdlib-libc++‘ )
3 except ValueError:
4      pass


至此，就可以使用YCM补全代码了。


