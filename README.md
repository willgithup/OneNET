the book is so greate about vim ide config.

for me; something diffirent about the env.
1   ubuntu + xshell + and the color scheme for xshell is solarized.

2    diffrent things with the book
     set background=dark
     colorscheme solarized  are comment by me.
     
     set cursorline
     set cursorcolumn  are both added the "hi CursorLine cterm=NONE ctermbg=black ctermfg=green guibg=NONE guifg=NONE";
     
     let g:indent_guides_auto_colors = 0                                          
     autocmd VimEnter,Colorscheme * :hi IndentGuidesOdd  guibg=green ctermbg=black                                 
     autocmd VimEnter,Colorscheme * :hi IndentGuidesEven guibg=NONE ctermbg=black  are added for indent bar;
     
     http://blog.csdn.net/u014483177/article/details/53209109 solve the  vim  open errors。

