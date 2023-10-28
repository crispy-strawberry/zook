# Variables

## What are variables?
They can be said to be places in memory 
where the data of your program is stored.

## Variables in Zig
In Zig, variables are declared using the `const`
or `var` keywords. 

### Immutable
Variables whose value cannot change are declared using the `const` keyword.  
They are **immutable**.
```rs
pub fn main() void {
    const age = 23;
}
```

If you try reassigning a const variable,
the zig compiler will throw an error.
```rs
pub fn main() void {
    const year = 2023;

    year = 2023;
//  ^^^^ This will fail as you try to change the value of a constant
}
```

### Mutable
Variables whose value can change are declared using the `var` keyword.
The are **mutable** and their value can change.
```rs
pub fn main() void {
    var year = 2023;

    year = 2024;
//  ^^^^ year is a var, so its value can change.
}
```
