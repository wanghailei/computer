# Operate File

## **Modes of Vim**



```bash
:		# Put vim in last-line mode.
```

## Open Files



```bash
## Open Files

vi -o5		# Open 5 blank windows from top to bottom.
vi -O3		# Open 3 blank windows from left to right.

vi -O3 *		# Open 3 windows from left to right and show the first 3 files or subdirectories.
vi -O *		# Open all each file and subdirectory in a window from left to right.

vi -o f1.rb f2.rb f3.rb		# Open each file in a window from top to bottom.
vi -O f1.rb f2.rb f3.rb		# Open each file in a window from left to right.

```



## Creat a new file



### Turn the selected(highlighted with V) lines into a new file

```bash
:w newfilename.css
```



## Save File

```bash
## Save

:q		# Close one file at a time.
wq		# Save and quite file
ZZ     	# Save and quit file. Save and close all these windows simutaniusly?

```



# Directory / Folder

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
