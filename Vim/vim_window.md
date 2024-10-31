# **Window**

```bash
:vsp					# Split into a new window vertically and evenly.
:sp					# Split into a new window horizontally and evenly.

:vertical resize n		# Set the current window’s width to n. (n is a percentage to the current size.)

:30winc <				# Decrease the current window column’s width by 30.
```





## Move among windows

```bash
## Move 

CTRL-w, CTRL-w		# Cycle through windows.

CTRL-w, h j k l		# Move to a window in a direction.



CTRL-w, then < or >      Decrease and increase the window width.

CTRL-w, then |       Maximize the current window’s width possibly.

CTRL-w, then =       Equalize all windows’ sizes

Ctrl-w q will close the active window.

Ctrl-w r will rotate windows to the right.

Ctrl-w R will rotate windows to the left.
```







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



