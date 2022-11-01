# Notes for Week 1 (C)

## Table of contents:
1. [General](#general)
2. [C Related](#c-related)
    1. [General](#general)
    2. [Coding](#coding)
        1. [Printing](#1-printing)
        2. [Data Types and Variables](#2-data-types-and-variables)
            1. [Data Types](#a-data-types)
            2. [Variables](#b-variables)
            3. [Variables with different data types](#c-variables-with-different-data-types)
            4. [User Input](#d-user-input)
            5. [Overwriting Variables and Constant Variables](#e-overwriting-variables-and-constant-variables)
        3. [Arithmetics Operators, Formatting and Typecasting](#3-arithmetics-operators-formatting-and-typecasting)
            1. [Arithmetic Operators](#a-arithmetic-operators)
            2. [Using Arithmetic Operators](#b-using-arithmetic-operators)
        4. [Conditionals and Logical Operators](#4-conditionals-and-logical-operators)
            1. [Types of Conditional Operators](#a-types-of-conditional-operators)
            2. [Conditional Statements](#b-conditional-statements)
            3. [Logical Operators](#c-logical-operators)

<br>

## **General**
---

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
---

### General
======
- File that holds C codes ends with **.c**.
- C codes are compiled using the command `make filename`
  - filename ends with .c but not required to be used when compiling
  - everytime change is made, the `make` command must be re-run
- compiled file is run using `./filename`
  - `./` means in current directory
  - `filename` is same as the .c filename without the extension

<br/>

### Coding
======
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

<br>

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

#### **a. Data Types**

- `hello world` printed earlier is a type of data called `string`
- the data types that are available in C are:
  - `string` (more than 1 characters)
  - `char` (exactly 1 character)
  - `int` (integers, both positive and negative)
  - `long` (larger range of `int`)
  - `float` (decimal numbers)
  - `double` (larger range of `float`)
  - `bool` (only has 2 values: `True` or `False`)

<br>

#### **b. Variables**
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

<br>

#### **c. Variables with different data types**
- different variable types have the variables written differently.
- Examples are as following:
  - `string` (more than 1 characters)
    ```c
    string name = "James";
    ```
  - `char` (exactly 1 character)
    ```c
    char enabled = 'Y';
    ```
  - `int` (integers, both positive and negative)
    ```c
    int age = 23;
    ```
  - `long` (larger range of `int`)
    ```c
    long money = 22000000;
    ```
  - `float` (decimal numbers)
    ```c
    float weight = 65.5;
    ```
  - `double` (larger range of `float`)
    ```c
    double measurement = 45.555;
    ```
  - `bool` (only has 2 values: `True` or `False`)
    ```c
    bool protected = True;
    ```
- Note that only `string` and `char` are enclosed in quotes.
  - `string` => always double quotes
  - `char` => always single quotes 

<br>

#### **d. User Input**

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

<br>

#### **e. Overwriting Variables and Constant Variables**
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
- Values that are assigned within the code are usually code "magic number".
  - if possible, hard coding values should be avoided unless it's a fixed value that won't change.
  - commonly values are assigned into variables via input or other operations.
- variables that should not be overwritten or kept constant should be declared/initialized with `const`. constant variables' name are usually written in all caps:
    ```c
    const int NAME = "James";
    ```

<br>

#### **3. Arithmetics Operators, Formatting and Typecasting**

#### **a. Arithmetic Operators**
- there are 5 arithmetic operators:
  - `+` (addition)
  - `-` (subtraction)
  - `*` (multiplication)
  - `/` (division)
  - `%` (modulus)
- A division operator gives the value of the quotient whereas modulus operator gives the value of the remainder.

<br>

#### **b. Using Arithmetic Operators**
- Examples of arithmetic operations:
  - Using only integers
    ```c
    // filename will be int_op.c
    #include <stdio.h>

    int main(void)
    {
      // using int only
      int added = 1 + 1;
      int subtracted = 4-2;
      int multiplied = 2*7;
      int divided = 5/3;
      int remainder = 5%3;

      printf("Added value is %i\n", added);
      printf("Subtracted value is %i\n", subtracted);
      printf("Multiplied value is %i\n", multiplied);
      printf("Divided value is %i\n", divided);
      printf("Remainder value is %i\n", remainder);
    }
    ```
    - This outputs:
      ```shell
      Added value is 2
      Subtracted value is 2
      Multiplied value is 14
      Divided value is 1
      Remainder value is 2
      ```
      - Note: for divided 5/3, we get 1 (the quotient, top value). For same operation, if we use operator, we get 2 (the remainder, bottom value). Both are shown below

          $\begin{array}{r}
          1\phantom{)}   \\
          3{\overline{\smash{\big)}\,5\phantom{)}}}\\
          \underline{-~\phantom{(}(3)}\\
          2\phantom{)}\\ 
          \end{array}$

  - Using only decimals
    ```c
    // filename will be dec_op.c
    #include <stdio.h>

    int main(void)
    {
      // using decimals only
      float added = 1.2+ 1.5;
      float subtracted = 4.3-2.9;
      float multiplied = 2.1*7;
      float divided = 5.3/3;
      //float remainder = 5.3 % 3.0; //this gives error as % is an integer operation
      
      //printing as it is
      printf("Added value is %f\n", added);
      printf("Subtracted value is %f\n", subtracted);
      printf("Multiplied value is %f\n", multiplied);
      printf("Divided value is %f\n", divided);

      // adding space between two printouts
      printf("\n");

      // printing with small addition in formatting
      printf("Added value is %.2f\n", added);
      printf("Subtracted value is %.2f\n", subtracted);
      printf("Multiplied value is %.2f\n", multiplied);
      printf("Divided value is %.2f\n", divided);
    }
    ```
    - This outputs:
      ```shell
      Added value is 2.700000
      Subtracted value is 1.400000
      Multiplied value is 14.700000
      Divided value is 1.766667

      Added value is 2.70
      Subtracted value is 1.40
      Multiplied value is 14.70
      Divided value is 1.77
      ```
      - float and float results in float end value. float and integer also result in float end value.
      - `%.2f` => `%f` is placeholder for float variable. `.2f` means 2 decimal places.
      - if 4 decimal places is need, it'll be `%.4f`
  - You can convert numbers from one type to another type by typecasting.
    - It is done by putting the new type to be casted into infront of the variable you want to convert to.
      ```c
      // filename will be int_op.c
      #include <stdio.h>

      int main(void)
      {
        int x = 2;
        int y = 4;

        // required multiplication result in 2 decimal places.
        // storing answer in new variable and printing it
        // you can type cast both x and y or either but stored variable 
        // must be of type float.
        float z = (float) x * (float) y;

        printf("The multiplication value is %.2f\n", z);
      }
      ```
    - This outputs:
      ```shell
      The multiplication value is 8.00
      ```

<br>

#### **4. Conditionals and Logical Operators**
- To execute codes only when certain condition is fulfilled, a conditional statement can be used.
- conditional statements are compared using conditional operators

<br>

#### **a. Types of Conditional Operators**
- the conditional operators are:
  - `>` (greater than)
  - `>=` (greater than or equals to)
  - `<` (less than)
  - `<=` (less than or equals to)
  - `==` (equals to, check if its the same)
  - `!=` (inequality, check if its different)
- the result of a conditional statement is always `bool` that is either `True` or `False`. If `True`, the block under the statement is executed, else skipped.

<br>

#### **b. Conditional Statements**

- The syntax is
    ```c
    if (condition)
    {
        // do this code
    }
    ```

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

<br>

#### **c. Logical Operators**

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
      ```

<br>

#### **5. Loops**
