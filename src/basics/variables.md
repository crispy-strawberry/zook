# Variables

## What are variables?
They can be said to be places in memory 
where the data of your program is stored.

## Variables in Zig
In Zig, variables are declared using the `const`
or `var` keywords. 

Variables whose value cannot change are declared using the `const` keyword.  
They are **immutable**.
```rs
pub fn main() void {
    const a = 23;
}
```
