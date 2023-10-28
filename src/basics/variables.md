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
```rust
pub fn main() void {
    const age = 23;
    
    // Just ignore this for now
    _ = age;
}
```

If you try reassigning a const variable,
the zig compiler will throw an error.
```rust
pub fn main() void {
    const year = 2023;

    year = 2023;
//  ^^^^ This will fail as you try to change the value of a constant
}
```

### Mutable
Variables whose value can change are declared using the `var` keyword.
The are **mutable** and their value can change.
```rust
pub fn main() void {
    // Here, we specify the data type of the year
    var year: i32 = 2023;

    year = 2024;
//  ^^^^ year is a var, so its value can change.
}
```


### General
By default, zig throws an error if a variable is declared
but it is not used. That is why we used
`_ = age` in the first example as we don't use it.

All variables have a data type. It can be explicitly set 
by adding `: <datatype>` after the variable name.
```rust
# pub fn main() {
    const x: u32 = 45;
//  ^^^^^^^^^^^^ x is constant which type is 
//  an unsigned integer whose size is 32 bits.
# }
```

