# **Edit the text**

## **Move the cursor**



```bash
``		# Return to the original position - where the last G was issued. 
gd		# Move to definition or first occurrence of the word under cursor.
```

### **Move by screen**

```bash
## Move by screen

H		# Move to the top line of the screen.
M		# Move to the middle of the screen.
L		# Move to the bottom line of the screen.

CTRL-f	# Jump forward one full screen.
CTRL-b	# Jump backwards one full screen.

gg		# Go to the first line of the file
G		# Go to the last line of the file
[		# Go to the first line of the file, according to my test.
]		# Go to the last line of the file, according to my test.

zt		# Move the current line to the top of the screen.
zb		# Move the current line to the bottom of the screen.
zz		# Move the current line to the middle of the screen.
```

### **Move by lines**

```bash
## Move by lines

44G		# Go to the 44th line

{		# Move to the beginning of the current paragraph. 就是移動到上一個空行。
}		# Move to the beginning of the next paragraph. 就是移動到下一個空行。
%		# Move to a matching opening or closing parenthesis, square bracket or a curly brace.

\-		# Move to the beginning of the previous line.
\+		# Move to the beginning of the next line.

0		# Move to the beginning of the current line
$		# Move to the end of the current line

^		# Move to the first non blank character of the line.

```

### **Move by characters and words**

```bash
## Move by characters and words

w		# Forward by word.
W		# Move to the next word.
b		# Backward by word.
B		# Move to the previous word.

```

## **Insert**

```bash
## Insert

o		# Open new line below cursor to insert.
O		# Open new line above cursor to insert.
i		# Inser text at cursor
I		# Insert text at beginning of the current line
```

## **Copy**

```bash
## Copy

yy		# Yank(copy) the current line
4yy		# Yank 4 lines
y$		# Yank from the cursor to the end of the line
yw		# Yank the current word under cursor

yi'		# Copy text inside ''.
ya(		# Copy text inside the () as well as the ().

ggyG		# Go to the first line and yank to the last line.
:%y		# Yank the whole file lines.
```

### Copy to the system clipboard

```bash
"*y		# Copy the selected text, and put it into system clipboard register, 
		# and ready to paste outside of Vi. 
```

## **Paste**

```bash
## Paste

p		# Put(Paste) the yanked text below the cursor line.
P		# Put(Paste) the yanked text above the cursor line.

:e		# Same as above

vep		# Pasting over a word. Visual select to the End and Put. 
		# Copy over a word; move to the target word and.

1vp		# pasting over an entire block. 
		# Suppose you have yanked some text and you want to overwrite another area of text. 
		# A number before the v tells vim to use an area equal to the yanked text, multiplied by that number).	
```



### Paste from the system clipboard into Vim

```bash
"+p		# In the normal mode, paste at the cursor position.
```

In the **insert mode**, just **Cmd + V** on macOS.

## Join

```bash
J		# 將从cursor位置到行未的字符，貼到上一行的末尾（但有個空格，不知道為什麼）。
		# Takes the line below and joins it on to the current one.
```

## Delete

```bash
## Delete

dd		# Delete the current line.
d0		# Delete to the beginning of the current line.
D		# Delete to the end of the current line.
2dd		# Delete 2 lines   



deleting (cutting) them (da', di<, etc.) before pasting somewhere else.

## Quick delete, when in Insert mode:

CTRL + h		# Back one character.
CTRL + w		# Back one word.
CTRL + u		# Back to the beginning of the line.
```

## **Select**

```bash
## Select

v			# Visual Mode, select the current character of the cursor. 然後橫向移動可以選中更多字符。
V			# Visual Mode, select the current line of the cursor. 然後上下移動可以選中更多行。
vi( / vib	# Select text inside parentheses.
va( / vab 	# Select text including the parentheses.
vi[
va[ 
vi<
va<
vi"
va"

```

## Vertical Selection

```bash
Ctrl+v		# To enter the Visual Block Mode:

e			# To select the current word. then move downward or upward.

E			# To select the characters to the end of the line, then move downward or upward.

r			# To replace the selection.

I			# To insert characters. Note: it must be a cap I.
```







## Case

```bash
~		# Toggle case.
```

## **Undo & Redo**

```bash
u		# Undo last change
U 		# Undo the changes on the whole current line

Ctrl-r	# Redo a change that has been undone.
.		# Repeat last change, this is super useful when doing a repetitive task.

```

## Indent

```bash
>>		# Indent the current line.
<<		# Un-indent the current line.

5>>		# Indent 5 lines including the current line

=i{		# Re-indents "inner block" (inside the braces).
=a{		# Re-indents "a block" (including the braces).
=2a{		# Re-indents 2 blocks (this block and containing block).

gg=G    Indent all the content. (I tried, it works well. :-))

```

## **Re-formatting paragraphs or chunks of code**

```bash
V=		# Select text, then reformat.

=		# Correct alignment of code
==		# One line;

gq		# Reformat paragraph

:set ft=html		# To reformat HTML files, run this command first, then use V=.

```
