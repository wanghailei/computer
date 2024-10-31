# Vim Settings

## Disable mouse

In Vim, the set mouse= option controls how and when the mouse is enabled within the editor. The mouse setting can take various flags that specify in which modes mouse usage should be enabled. Here’s a breakdown of the options you can set:





​	3.	**Disable mouse support completely**:

```bash
set mouse=	" Disable mouse support completely
```





**set mouse=a (All modes)**



​	•	Enables the mouse in **all modes**: normal, insert, visual, command-line, and more. This is the most commonly used option if you want full mouse support.



**set mouse=n (Normal mode)**



​	•	Enables mouse support only in **normal mode**. You can select text, resize splits, etc., but the mouse will be disabled in other modes (insert, visual, etc.).



**set mouse=v (Visual mode)**



​	•	Enables mouse support only in **visual mode**. This allows you to use the mouse for selecting text visually.



**set mouse=i (Insert mode)**



​	•	Enables mouse support only in **insert mode**. This could be useful if you want to click into insert mode but avoid mouse functionality elsewhere.



**set mouse=c (Command-line mode)**



​	•	Enables mouse support only in **command-line mode**, which is when you are typing :commands.



**set mouse=r (Replace mode)**



​	•	Enables mouse support only in **replace mode**, which is less frequently used.



**set mouse="" (Disable mouse)**



​	•	Completely disables mouse support in Vim, so the mouse will have no effect at all inside the editor. This is the default mode, and the one you’d use to rely on keyboard navigation exclusively.



**Combining Modes**



You can combine these modes by listing them together. For example:



​	•	set mouse=nv enables the mouse in **normal** and **visual** modes.

​	•	set mouse=nic enables the mouse in **normal**, **insert**, and **command-line** modes.



**Example Configurations:**



​	1.	**Full mouse support** (all modes):



set mouse=a





​	2.	**Mouse only in normal and visual mode**:



set mouse=nv







By setting the appropriate flags, you can control how Vim handles mouse interaction to suit your preferences.