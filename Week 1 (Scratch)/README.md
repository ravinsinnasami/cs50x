# Notes for Week 1 (C)

## **General**

- Language that computer speak is binaries (1 and 0).
- IDE (Integrated Development Enviroment) are tools used to write programs.
  - VS Code is a commonly used software for coding.
- Source Code => code that you type.
- Machine Code => Source code that is converted into binaries.
- Source code converted to machine code using compiler.
  - Not all languages use compiler.

<br/>
<br/>


## **C Related**
### <u>General</u>
- File that holds C codes ends with **.c**.
- C codes are compiled using the command `make filename`
  - filename ends with .c but not required to be used when compiling
- compiled file is run using `./filename`
  - `./` means in current directory
  - `filename` is same as the .c filename without the extension

<br/>


### <u>Coding</u>
- A C coding file requires
  - header(s)
  - the main function
- C file main Syntax

    ```c
    // this is the header
    #include <stdio.h>

    // this is the main function
    int main(void)
    {
        // code here
    }
- For CS50, there is an additional header:
    ```c
    #include <cs50.h>
    ```

<br>

- First program printed is traditionally: `Hello World`.

    > Creating a file called hello.c

    ```c
    #include <stdio.h>
    
    int main(void)
    {
        printf("hello, world\n");
    }
    ```

    > compiling and running the file. 
    
    > Line 1 compiles, Line 2 runs the compiled file. Line 3 is output. Line 4 is next prompt.

    ```shell
    1 $: make hello
    2 $: ./hello
    3 hello, world
    4 $:
    ```

- printing in C is done using `printf("");`
  - items to be printed are enclosed within double quotes
- code lines usually end with semicolon, with some exceptions
- `\n` in the print inserts a newline
    - without `\n` in the statement, the output would be:

    > Line 4 is now together with line 3

    ```shell
    1 $: make hello
    2 $: ./hello
    3 hello, world$:
    ```