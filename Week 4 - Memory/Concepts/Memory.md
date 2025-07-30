Just as in the real world that mailboxes have unique addresses, also memory has addresses but the addresses in the memory are a lot more simple like: 0, 1, 2, 3....

To be able to poke around in the memory of our computer we will need some new building blocks:

**`&`** - If you use the & (once and not twice) and next to it you put a variable it will give you the address of that variable:

For example:

```
#include <stdio.h>
  
int main(void)
{
    int n = 50;
    printf("%p\n", &n);
}

-------------------------------------------------------------------
TERMINAL

make adresses
./adresses
0x7ffcb86b3ccc
```

The **`%p`** represents something called a pointer which is basically just resembling the address of said variable


**`*`** - The star operator is not multiply in this context but it's doing the opposite of the &:
You give it an address it will give you the value of that address.


#### **Pointers**

A _pointer_ is a variable that stores the address of something. Most succinctly, a pointer is an address in your computer’s memory.

You can make a pointer variable like this:
```
int n = 50;
int *p = &n;
```
to define a pointer, next to the type your write `*` which says that this variable is a pointer, notice that the type of the pointer is int because the type of the value of the address it contains is also an int:

`p` is the **pointer** and it contains the address of `n`
`n` is an int therefore the type of `p` must be an `int` too


Here is a :
```
// Stores and prints an integer's address
  
#include <stdio.h>
   
int main(void)
{
    int n = 50;
    int *p = &n;
    printf("%p\n", p);
    
}
```
Notice that this code has the same effect as our previous code. We have simply leveraged our new knowledge of the `&`and `*` operators. Notice that we used `%p` to print a **pointer**. The `p` stands for **pointer**

To illustrate the use of the `*` operator, consider the following:
```
// Stores and prints an integer via its address
#include <stdio.h>

int main(void)
{
    int n = 50;
    int *p = &n;
    printf("%i\n", *p);
}
```

Notice that the `printf` line prints the integer at the location of `p` because of the `*` before the variable. `int *p` creates a pointer whose job is to store the memory address of an integer.
The `*` declares a **pointer** only when you define a variable.


#### **Strings**
Now that we have a mental model for pointers, we can peel back a level of simplification that was offered earlier in this course.
Modify your code as follows:
```
// Prints a string

#include <cs50.h>
#include <stdio.h>
 
int main(void)
{
    string s = "HI!";
    printf("%s\n", s);
}
```

Notice that a string `s` is printed.

Recall that a string is simply an array of characters. For example, `string s = "HI!"` can be represented as follows:
 ![The string HI with an exclamation point stored in memory](https://cs50.harvard.edu/x/notes/4/cs50Week4Slide085.png "hi")
 
However, what is `s` really? Where is the `s` stored in memory? As you can imagine, `s` needs to be stored somewhere. You can visualize the relationship of `s` to the string as follows:

![Same string HI with a pointer pointing to it](https://cs50.harvard.edu/x/notes/4/cs50Week4Slide086.png "hi pointer")

Notice how a pointer called `s` tells the compiler where the first byte of the string exists in memory.

Modify your code as follows:
```
// Prints a string's address as well the addresses of its chars

#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string s = "HI!";
    printf("%p\n", s);
    printf("%p\n", &s[0]);
    printf("%p\n", &s[1]);
    printf("%p\n", &s[2]);
    printf("%p\n", &s[3]);
}
```

Notice the above prints the memory locations of each character in the string `s`. The `&` symbol is used to show the address of each element of the string. When running this code, notice that elements `0`, `1`, `2`, and `3` are next to one another in memory.
 
Likewise, you can modify your code as follows:
 
```
// Declares a string with CS50 Library
 
#include <cs50.h>
#include <stdio.h>
    
int main(void)
{
    string s = "HI!";
    printf("%s\n", s);
}
```

Notice that this code will present the string that starts at the location of `s`. This code effectively removes the training wheels of the `string` data type offered by `cs50.h`.This is raw C code, without the scaffolding of the cs50 library.

Taking off the training wheels, you can modify your code again:

```
// Declares a string without CS50 Library

#include <stdio.h>

int main(void)
{
    char *s = "HI!";
    printf("%s\n", s);
}
```

Notice that `cs50.h` is removed. A string is implemented as a `char *`.
You can imagine how a string, as a data type, is created.
Last week, we learned how to create your own data type as a struct.
The cs50 library includes a struct as follows: `typedef char *string`
This struct, when using the cs50 library, allows one to use a custom data type called `string`.