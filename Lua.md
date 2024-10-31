**Study Lua**





**Type**



Lua is a dynamically-typed language. 

There are no type definitions in Lua; each value carries its own type. 



**Nil**



Nil is a type with a single value, nil, whose main property is to be different from any other value. 

Lua uses nil as a kind of non-value, to represent the absence of a useful value. 

A global variable has a nil value by default, before its first assignment, and we can assign nil to a global variable to delete it. 



**Numbers**



Both integer and float values have type "number" 



Programmers can mostly ignore the difference between integers and floats. 



When we ignore these differences, we also can ignore the differences between Lua 5.3 and Lua 5.2.The main incompatibility between Lua 5.3 and Lua 5.2 is the representation limits for integers. 













The == operator tests for equality; the ~= operator is the negation of equality. 





**Numbers**



Strings represent text. A string in Lua can contain a single letter or an entire book. 



Strings in Lua are sequences of bytes. 



Strings in Lua are immutable values. 



We can concatenate two strings with the concatenation operator .. (two dots). 







**Tables**



Tables are the main (in fact, the only) data structuring mechanism in Lua. 



Tables are used to represent arrays, sets, records, and many other data structures in a simple, uniform, and efficient way. Lua uses tables to represent packages and objects as well. 



A table in Lua is essentially an associative array. 





Tables in Lua are neither values nor variables; they are objects. 



A table is always anonymous. There is no fixed relationship between a variable that holds a table and the table itself.



Like global variables, we can assign nil to a table field to delete it. This is not a coincidence: Lua stores global variables in ordinary tables. 



we can nest tables (and constructors) to represent more complex data structures. 





**Function**



Tabl





If the function has one single argument and that argument is either a literal string or a table constructor, then the parentheses are optional. An expression like o:foo(x) calls the method foo in the object o. 



A Lua program can use functions defined both in Lua and in C (or in any other language used by the host application). All functions from the standard Lua libraries are written in C. However, when calling a function, there is no difference between functions defined in Lua and functions defined in C. 



We can call a function with a number of arguments different from its number of parameters. Lua adjusts the number of arguments to the number of parameters by throwing away extra arguments and supplying nils to extra parameters. 



In Lua, functions can return multiple results. 