

**Search**



/xyz    Search xyz text pattern

n     Repeat search

N     Repeat search in opposite direction

\*     Search forward for a word under the cursor

\#     Search backward for a word under the cursor

:noh    clean the highlight text





**Search and Replace**

```bash
:s/eth0/br0/g		# Find and replace 'eth0' with ‘br0’, in the current line only.

:%s/eth1/br1/g		# Find and replace all occurrences of 'eth1' with 'br1'

:%s/eth1/br1/gi	# Find and replace all occurrences of 'eth1' with 'br1', case insensitive.

:3,7s/eth1/br1/g	# Find and replace all occurrences of 'eth1' with ‘br1', from lines from 3 to 7.
```









**Search and delete**



:g/George Bush/d     Find and then delete all lines containing the pattern "George Bush”.



Here's a brief explanation of how this vi/vim search and delete command works:

- The g characters says "perform the following operation globally in this file".
- The forward slash characters enclose the pattern I'm trying to match. In this case it's a very simple sequence of characters, but it can also be a more complicated regular expression.
- The d at the end of the command says "When you find this pattern, delete the line".



