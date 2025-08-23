#python

Humans, over the decades, have seen how previous design decisions made in prior programming languages could be improved upon.

Python is a programming language that builds upon what you have already learned in C.

Python additionally has access to a vast number of user-created libraries.

Unlike in C, which is a __[[Compiling|compiled language]]__, Python is an __interpreted language__, where you need not separately compile your program. Instead, you run your program in the __Python Interpreter__.

Up until this point, the code has looked like this:

```
    // A program that says hello to the world
    
    #include <stdio.h>
    
    int main(void)
    {
        printf("hello, world\n");
    }
```

Today, you’ll find that the process of writing and compiling code has been simplified.

For example, the above code will be rendered in Python as:
```
    # A program that says hello to the world
    
    print("hello, world")
```

Notice that the semicolon is gone and that no library is needed. You can run this program in your terminal by typing `python hello.py`.

Python notably can implement what was quite complicated in C with relative simplicity.


[[Speller]]