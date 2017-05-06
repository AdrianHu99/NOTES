1. The difference between `const`, `var` and `let`:   

`const` is a signal that the identifier won’t be reassigned.   


`let`, is a signal that the variable may be reassigned, such as a counter in a loop, or a value swap in an algorithm. It also signals that the variable will be used only in the block it’s defined in, which is not always the entire containing function.  


`var` is now the **weakest signal available** when you define a variable in JavaScript. The variable may or may not be reassigned, and the variable may or may not be used for an entire function, or just for the purpose of a block or loop.

2. The difference between **for...in** loop and **for(i;i < x; i++)** loop:   

`For..in` loop is for enumeration, it should not be used for array-like objects. The order of iteration is not guaranteed, the array indexes may not be visited in numeric order. And inherited properties are also enumerated. In short, it is looping object's properties.

`For(i..)` loop is for iteration.

3. 
