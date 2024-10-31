

### Open the Explorer

`:E`

in the `:E` state, press `q` or input `:b#` to exit back to the previous buffer.

























**Learning Vi**











**Modes of Vim**



:     Put vim in last-line mode.



:%y    Yank the whole file lines.

:%     Refer the next command to work on all the lines ???



.     Repeat last change, this is super useful when doing a repetitive task.

Open Files





vi -o5    Open 5 blank windows from top to bottom.

vi -O3    Open 3 blank windows from left to right.



vi -o 	 f1.rb f2.rb f3.rb    Open each file in a window from top to bottom.

vi -O 	 f1.rb f2.rb f3.rb    Open each file in a window from left to right.



vi -O *    Open all each file and subdirectory in a window from left to right.
        ZZ will save and close all these windows simutaniusly. 

​       :q will close one file at a time.



vi -O3 *   Open 3 windows from left to right and show the first 3 files or subdirectories.









**Move the cursor**





``     Return to the original position - where the last G was issued 

gd     Move to definition or first occurrence of the word under cursor.





**Move by screen**



H		Move to the top line of the screen

M		Move to the middle of the screen

L     Move to the bottom line of the screen

CTRL-f   Jump forward one full screen/page.

CTRL-b   Jump backwards one full screen/page.

gg     Go to the first line of the file

G     Go to the last line of the file





**Move by lines**



44G    Go to the 44th line



{     Move to the beginning of the current paragraph, 就是移動到上一個空行

}     Move to the beginning of the next paragraph, 就是移動到下一個空行

   

\-     the beginning of the previous line

\+     the beginning of the next line

0     the beginning of the current line

$     the end of the current line

^     Go to the first non blank character of the line.



%     Jump to a matching opening or closing parenthesis, square bracket or a curly brace.



**Move by characters and words**



w     Forward by word

W     Go to the next WORD. (WORD consists of a sequence of non-blank characters, separated with white space.)

b     Backward by word

B     Go to the previous WORD. 



**Edit the text**



**Insert**



o     Open new line below cursor

O     Open new line above cursor

i     Inser text at cursor

I     Insert text at beginning of the current line



**Copy**



yy     Yank(copy) the current line

4yy    Yank 4 lines

y$     Yank from the cursor to the end of the line

yw     Yank the current word under cursor

ggyG    Go to the first line and yank to the last line.

:%y    Yank the whole file lines.



\+  	 Copy to the system clipboard ???



**Paste**



p     Put(Paste) the yanked text below the cursor line

P     Put(Paste) the yanked text above the cursor line

:e #    Same as above



**Join**



J     将cursor位置到行未的字符贴到上一行的末尾（但有个空格，不知道为什么）。





**Delete**



dd     Delete the current line

d0     Delete to the beginning of the current line

D     Delete to the end of the current line

2dd    Delete 2 lines   



**Case**



~     Toggle case







**Undo & Redo**



u     Undo last change

U     Undo the changes on the whole current line

Ctrl-r   Redo a change that has been undone.

.     Repeat last change, this is super useful when doing a repetitive task.





**Save File**



wq     Save and quite file

ZZ     Save and quit file



**Select**



v     Visual Mode, select the current character of the cursor. 然后横向移动可以选中更多字符

V     Visual Mode, select the current line of the cursor. 然后上下移动可以选中更多行



vi( or vib will select text inside parentheses; va( or vab will select including the parentheses.

Similarly for vi[, va[, vi<, va<, etc.



Consider also skipping the selection step, and just yank (copy) them (yi', ya(, etc.) or deleting (cutting) them (da', di<, etc.) before pasting somewhere else.



**Indent**



\>>     Indent the current line

<<     Un-indent the current line

5>>    Indent 5 lines including the current line

=i{    Re-indents "inner block" (inside the braces).

=a{    Re-indents "a block" (including the braces).

=2a{    Re-indents 2 blocks (this block and containing block).

gg=G    Indent all the content. (I tried, it works well. :-))





**Re-formatting paragraphs or chunks of code**



V=     select text, then reformat with =

=     correct alignment of code

==     one line;

gq     reformat paragraph

:set ft=html   TO reformat HTML files, run this command first, then use V=

   



**Search**



/xyz    Search xyz text pattern

n     Repeat search

N     Repeat search in opposite direction

\*     Search forward for a word under the cursor

\#     Search backward for a word under the cursor

:noh    clean the highlight text





**Search and Replace**



:s/eth0/br0/g      Find and replace 'eth0' with ‘br0’, in the current line only.

:%s/eth1/br1/g  		Find and replace all occurrences of 'eth1' with 'br1'

:%s/eth1/br1/gi    Find and replace all occurrences of 'eth1' with 'br1', case insensitive.

:3,7s/eth1/br1/g     Find and replace all occurrences of 'eth1' with ‘br1', from lines from 3 to 7.





**Search and delete**



:g/George Bush/d     Find and then delete all lines containing the pattern "George Bush”.



Here's a brief explanation of how this vi/vim search and delete command works:

- The g characters says "perform the following operation globally in this file".
- The forward slash characters enclose the pattern I'm trying to match. In this case it's a very simple sequence of characters, but it can also be a more complicated regular expression.
- The d at the end of the command says "When you find this pattern, delete the line".





**Window**



:vsp           Split into a new window vertically and evenly.

:vs

:sp           Split into a new window horizontally and evenly.

:vertical resize n    Set the current window’s width to n. (n is a percentage to the current size.)



:30winc <  				  Decrease the current window column’s width by 30.



CTRL-w CTRL-w      Cycle through windows

CTRL-w h j k l      Move to a window in a direction



CTRL-w, then < or >      Decrease and increase the window width.

CTRL-w, then |       Maximize the current window’s width possibly.

CTRL-w, then =       Equalize all windows’ sizes

Ctrl-w q will close the active window.

Ctrl-w r will rotate windows to the right.

Ctrl-w R will rotate windows to the left.



**Netrw**





**Launch Netrw Window**



These commands don’t even need a space between it and its arguments, so its very few keystrokes:



:E			Open the directory of the current file.

:e .			Open the directory of the current file normally.

:rew			Open the directory



:sp.			Open the current directory in a horizontal split

:vs.			Open the current directory in a vertical split



:Hex			Horizontal split

:Hex!			Horizontal split (opposite side)

:Vex			Vertical split

:Vex!			Vertical split (opposite side)

:Sex			Invoke a horizontal split.



:Tex			New tab, directory of currently open buffer



:Lex			Vertical split full height, current working directory

:Lex!			Vertical split, current working directory (opposite side)





**Directory Navigation**



Navigating around netrw is pretty intuitive, you use the arrows (or hjkl) to move around and enter to open files or directories. These windows are just like any other window in vim so most of the usual motions, etc. work except netrw adds some default mappings. Here are the basics for navigation:





-		Go up one directory

u		Go back to previously visited directory (like <C-o> in vim)

U		Go forward to subsequently visited directory (like <C-i> in vim)

x		Open the file/directory with the default system app





**Open files/directories**



enter		Open files/directories



v  	 When navigating a folder, hitting <v> opens a window at right side

% 这个非常好用，相当于单击文件列表中的一个文件名，从而在右侧窗口打开文件内容。 %



o		Open file/directory in new horizontal split



t		Open file/directory in new tab

% 我不使用Netrw自己的tab，而是使用 macOS Terminal的。%



p		Preview file without (moving the cursor from netrw)





**Manipulating Files in a directory**



%		Create a new file

d		Create a new directory

D		Delete a file

R		Rename



**Netrw Remote / Across networks**





**Remote Browsing**



​    :e [protocol]://[user]@hostname/path/ 

​    :Nread [protocol]://[user]@hostname/path/ 



​	--



​    :e dav://machine[:port]/path           uses cadaver 

​    :e fetch://[user@]machine/path         uses fetch 

​    :e ftp://[user@]machine[[:#]port]/path     uses ftp  autodetects <.netrc> 

​    :e http://[user@]machine/path          uses http uses wget 

​    :e rcp://[user@]machine/path         	uses rcp 

​    :e rsync://[user@]machine[:port]/path   	uses rsync 

​    :e scp://[user@]machine[[:#]port]/path    uses scp 

​    :e sftp://[user@]machine/path          uses sftp 



**Remote Reading**



​    :Nread ?                         	give help 

​    :Nread "machine:path"               	uses rcp 

​    :Nread "machine path"               	uses ftp  with <.netrc> 

​    :Nread "machine id password path"       uses ftp 

​    :Nread "dav://machine[:port]/path"        uses cadaver 

​    :Nread "fetch://[user@]machine/path"      uses fetch 

​    :Nread "ftp://[user@]machine[[:#]port]/path"  uses ftp  autodetects <.netrc> 

​    :Nread "http://[user@]machine/path"       uses http uses wget 

​    :Nread "rcp://[user@]machine/path"      	uses rcp 

​    :Nread "rsync://[user@]machine[:port]/path"  uses rsync 

​    :Nread "scp://[user@]machine[[:#]port]/path" uses scp 

​    :Nread "sftp://[user@]machine/path"     	uses sftp 



**REMOTE WRITING** 



​    :Nwrite ?                           give help 

​    :Nwrite "machine:path"                 uses rcp 

​    :Nwrite "machine path"                 uses ftp  with <.netrc> 

​    :Nwrite "machine id password path"      	uses ftp 

​    :Nwrite "dav://machine[:port]/path"         uses cadaver 

​    :Nwrite "ftp://[user@]machine[[:#]port]/path" 	uses ftp  autodetects <.netrc> 

​    :Nwrite "rcp://[user@]machine/path"        uses rcp 

​    :Nwrite "rsync://[user@]machine[:port]/path"  uses rsync 

​    :Nwrite "scp://[user@]machine[[:#]port]/path"  uses scp 

​    :Nwrite "sftp://[user@]machine/path"      	uses sftp 

​    http: not supported! 





**Configure Appearance and Behaviour**



One of the first things I noticed when making the switch was when you press enter on a directory, instead of displaying the contents of the sub-directory inline, it would replace the whole buffer with the contents of the sub-directory. This is because by default netrw doesn’t use a tree to display the files/directories, its more like doing an ls but you can configure netrw to print a tree and have the same behaviour as NERDTree with this mapping:



i - Cycle between different listing modes (one of them is tree mode)

- In normal mode, enter will move into and show the given file/directory
- In tree mode, enter will show the contents of the sub-directory in addition



While netrw doesn’t look as nice as NERDTree, it still has a lot of options to customize the way it looks and works.



I - Toggle the banner



c - Make the browsing directory the current working directory



gn - Make the directory under the cursor the top of the tree



gh - Toggle hidden files on or off



a - Cycle between all files, not hidden files or just hidden files visible



s - Cycle sort order between name, time or filesize

r - Reverse sort order



Copying files however is a little more involved. You need to mark the files you want to copy, mark the destination, then execute the operation (a little tedious):



mf - Toggle whether the file/directory is marked



mt - Mark the directory under the cursor as the copy target



mc - Execute the copy operation

mu - Unmark all marked items







![pastedGraphic.png](blob:file:///351dbfc9-c203-45ab-94ac-301afef2e4e3)



Quick delete from Insert mode



One thing I found frustrating (and time consuming) was that I would often need to switch from Insert to Normal mode every time I entered a typo (a frequent occurrence). Now I realise there is no need to. Instead, when in Insert mode:



CTRL + h back one character



CTRL + w back one word



CTRL + u back to the beginning of the line

These shortcuts have come in really handy.

Joining Lines



Use Shift+J to join two lines together. It takes the line below and joins it on to the current one.

Pasting over a word



It’s easier to copy over a word; move to the target word and vep (Visual select to the End and Put).

Copying and pasting over an entire block



I’m still not convinced this is the best way! However, the following seems to work quite well.

Suppose you have yanked some text and you want to overwrite another area of text (could be a different size). Move the cursor where you want the block and 1vp (a number before the v tells vim to use an area equal to the yanked text, multiplied by that number).

However, when you are replacing a large block of text with a small block having to ‘explain’ to Vim the size of the area seems nuts.
