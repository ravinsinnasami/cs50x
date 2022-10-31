# Notes for Week 1 (C)

## **General**

- Language that computer speak is binaries (1 and 0).
- IDE (Integrated Development Enviroment) are tools used to write programs.
  - VS Code is a commonly used software for coding.
- Source Code => code that you type.
- Machine Code => Source code that is converted into binaries.
- Source code converted to machine code using compiler.
  - Not all languages use compiler.
- codes are executed one after another from top to bottom.
  - There are some programming logics that can be applied to skip or execute certain codes depending on conditions.

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
    ```
    - `//` is used to write codes in C language. Anything typed after`//` is not processed/used/printed.
- For CS50, there is an additional header:
    ```c
    #include <cs50.h>
    ```

<br>

#### **1. Printing**
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
  - `printf()` is a function. Functions are code which can be used repeatedly that does a specific thing.
- code lines usually end with semicolon, with some exceptions
- `\n` in the print inserts a newline
    - without `\n` in the statement, the output would be:

    > Line 4 is now together with line 3

    ```shell
    1 $: make hello
    2 $: ./hello
    3 hello, world$:
    ```

<br>

#### **2. Data Types and Variables**
- `hello world` printed earlier is a type of data called `string`
- the data types that are available in C are:
  - `string` (more than 1 characters)
  - `char` (exactly 1 character)
  - `int` (integers, both positive and negative)
  - `long` (larger range of `int`)
  - `float` (decimal numbers)
  - `double` (larger range of `float`)
  - `bool` (only has 2 values: `True` or `False`)
- Variables can be looked as containers that hold information (specific data).
  - a variable need to be declared (created) with the appropriate data type to hold said value.
  - variable name is used to identify the variable and usually starts with uppercase or lowercase letter.
  - a variable is created by using the data type followed by a name => creating a variable called `age` with type `int`:
    ```c
    int age;
    ```

  - multiple variables of same type can be created at once
    ```c
    float weight, height;
    ```
    - separate each variable with comma and end with semicolon
  - A declared variable is usually empty unless it's assign with a value.
    - Value is assigned using the `=` symbol. 
    - For example, assigning value `43` to variable `age` (created above)
        ```c
        age = 43;
        ```
  - A variable can be declared and assigned value at the same time. It's called initialization. The differences shown:
    ```c
    // declare, then assigned
    float height;
    height = 173.2;

    // initialized at once
    float height = 173.2;
    ``` 
- Variables can also store information from user. This is done by getting input from user, storing in variable and subsequently, using/printing it.
  - CS50.h library has different functions that get input from user
  - Example of getting a name from user, storing it and then printing a greeting using given name in a file called `greet.c`
    ```c
    #include <stdio.h>
    #include <cs50.h>

    int main(void)
    {
        // get input from user and store in variable
        string name = get_string("What is your name? ");

        // print greeting for user
        printf("hello there, %s", name);
    }
    ```
  > The output
  ```shell
  1 $: make greet
  2 $: ./greet
  3 What is your name? Thor
  4 hello there, Thor
  5 $
  ```
  > `Thor` is user input.
  - `get_string` is function that obtains string from user. It is a function from cs50.h library
  - `printf("hello there, %s", name);` is a special way of formatting to enable usage of variable in printout.
    - `%s` is a placeholder. Variable that is passed in occupies the placeholder.
    - `"hello there, %s"` is the print statement. `name` is the variable that is passed in. Both are separated by a comma.
    - other placeholders include: `%c` for char, `%f` for float or double, `%i` for int.
- variables that are created thus far, can be overwritten. Example (`age.c`):
    ```c
    #include <stdio.h>
    #include <cs50.h>

    int main(void)
    {
        // initialize age
        int age = 23;

        printf("Current age: %i", age);

        printf("overwriting variable");

        // overwriting age
        age = 31;

        printf("Current age: %i", age);
    }
    ```
    > output would be:
    ```shell
    1 $: make age
    2 $: ./age
    3 Current age: 23
    4 overwriting variable
    5 Current age: 31
    ```
- variables that should not be overwritten or kept constant should be declared/initialized with `const`. constant variables are usually written in all caps:
    ```c
    const int NAME = "James";
    ```

<br>

#### **3. Conditionals and Operators**
- To execute codes only when certain condition is fulfilled, a conditional statement can be used.
- conditional statements are compared using conditional operators
- the conditional operators are:
  - `>` (greater than)
  - `>=` (greater than or equals to)
  - `<` (less than)
  - `<=` (less than or equals to)
  - `==` (equals to, check if its the same)
  - `!=` (inequality, check if its different)
- the result of a conditional statement is always `bool` that is either `True` or `False`. If `True`, the block under the statement is executed, else skipped.
- The syntax is
    ```c
    if (condition)
    {
        // do this code
    }
- Conditional statements can take into account multiple scenario; that is if first condition is not satisfied, check next, if not next until the last one. This is done using `if-else if-else` statements:
```c
if (age < 18)
{
    printf("teenager\n");
}
else if (age < 10)
{
    printf("toddler\n");
}
else{
    printf("baby\n");
}
```
> This checks if age is under 18, if yes, excute that code and exits. Else, goes to next one. else, prints the final one. In this code, age above 18 prints `baby`
  - If the last `else` is changed to `else if (age < 5) {printf("baby");}`, then the code does not print anything when age is above 18 (as no condition is satisfied).
  - If the code was as following:
  ```c
if (age < 5)
{
    printf("baby\n");
}
if (age < 10)
{
    printf("toddler\n");
}
if (age < 18)
{
    printf("teenager\n");
}
```
> checking against age 3, yield the following:
```shell
1 $: ./file
2 baby
3 toddler
4 teenager
```
> all 3 output is printed. Its because each if statement is separated, so, it checks each time. `if-else if-else` is counted as one whole thing. The moment one code is executed, it skips the rest.
- multiple conditions can be combined to get a more specific code execution.
  - conditions are combined using logical operators such as:
    - `&&` => and operator => check if two conditions are `True`
    ```c
    if (age < 23 && name = "James")
    {   
        //executes the code if age is 23 and name is James
    }
    ```
    - `||` => or operator => check if either one of the condition is `True`
    ```c
    if (height > 130 || height < 180)
    {
        // executes the code if the given height is above 130 or below 180; meaning in between that range
    }
    ```
    - `!` => not operator => reverses the Boolean value
    ```c
    if !(age < 23)
    {
        // when age is above 23, it returns False and the ! operator inverts it to True => executing this code block

        // if age is under 23, then the condition is True and the ! operater inverts to False => doesn't execute the code
    }

