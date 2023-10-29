# Basic Zig Project
Now that you have got zig up and running,
it's time to start a basic project in zig.

1. Create a new directory where you want to put the
new project. 
    ```bash
    mkdir my-zig-project && cd my-zig-project
    ```

2. Initialize a zig project in the current directory
    ```bash
    zig init-exe
    ```
    If you see something like
    ```
    info: Created build.zig
    info: Created src\main.zig
    info: Next, try `zig build --help` or `zig build run`
    ```
    then you have successfuly created a zig project.
    If not, then go through the installation section to 
    check if you made any mistakes.

3. Open the folder in a text editor.  
You should see a folder called `src`. This is where 
source code of your project lives.
    ```rust
    const std = @import("std");

    pub fn main() !void {
        // Prints to stderr (it's a shortcut based on `std.io.getStdErr()`)
        std.debug.print("All your {s} are belong to us.\n", .{"codebase"});

        // stdout is for the actual output of your application, for example if you
        // are implementing gzip, then only the compressed bytes should be sent to
        // stdout, not any debugging messages.
        const stdout_file = std.io.getStdOut().writer();
        var bw = std.io.bufferedWriter(stdout_file);
        const stdout = bw.writer();
        
        try stdout.print("Run `zig build test` to run the tests.\n", .{});
        
        try bw.flush(); // don't forget to flush!
    }

    test "simple test" {
        var list = std.ArrayList(i32).init(std.testing.allocator);
        defer list.deinit(); // try commenting this out and see if zig detects the memory leak!
        try list.append(42);
        try std.testing.expectEqual(@as(i32, 42), list.pop());
    }
    ```
    For now, remove everything from `test "simple test" {`
    Now, lets go step by step throught the file.

## main.zig
1. The first line in `main.zig` is 
    ```rust
    const std = @import("std");
    ```
    `const` is used to declare constant named `std`.  
    `@import("std")` tells the zig compiler that we want to import the 
    The Zig Standard Library is needed for things like printing
    to stdout, opening files, networking etc.

2. ```rust
    pub fn main() void {} 
    ``` 
    is used to declare a function.  
    The `fn` keyword declares a function and main is the name 
    of the function.  
    The return type comes after `main()`. Here, the return type 
    is `void`. `void` basicaly means we don't have anything to 
    return.  
    `main` is a special function that is excuted when the executable
    is run. It is the entry point of the executable.

