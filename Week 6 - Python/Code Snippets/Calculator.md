#code-snippet #python 

You might recall `calculator.c` from earlier in the course:
```
// Addition with int
    
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Prompt user for x
        int x = get_int("x: ");
    
        // Prompt user for y
        int y = get_int("y: ");
    
        // Perform addition
        printf("%i\n", x + y);
    }
```

We can implement a simple calculator just as we did within C. Type `code calculator.py` into the terminal window and write code as follows:
```
    # Addition with int [using get_int]
    
    from cs50 import get_int
    
    # Prompt user for x
    x = get_int("x: ")
    
    # Prompt user for y
    y = get_int("y: ")
    
    # Perform addition
    print(x + y)
```
    
Notice how the CS50 library is imported. Then, `x` and `y` are gathered from the user. Finally, the result is printed. Notice that the `main` function that would have been seen in a C program is gone entirely! While one could utilize a `main` function, it is not required.

It’s possible for one to remove the training wheels of the CS50 library. Modify your code as follows:
```
    # Addition with int [using get_int]
    
    from cs50 import get_int
    
    # Prompt user for x
    x = get_int("x: ")
    
    # Prompt user for y
    y = get_int("y: ")
    
    # Perform addition
    print(x + y)
```

Notice how the CS50 library is imported. Then, `x` and `y` are gathered from the user. Finally, the result is printed. Notice that the `main` function that would have been seen in a C program is gone entirely! While one could utilize a `main` function, it is not required.

It’s possible for one to remove the training wheels of the CS50 library. Modify your code as follows:
```
    # Addition with int [using input]
    
    # Prompt user for x
    x = input("x: ")
    
    # Prompt user for y
    y = input("y: ")
    
    # Perform addition
    print(x + y)
```

Notice how executing the above code results in strange program behavior. Why might this be so?

You may have guessed that the interpreter understood `x` and `y` to be strings. You can fix your code by employing the `int` function as follows:
```
    # Addition with int [using input]
    
    # Prompt user for x
    x = int(input("x: "))
    
    # Prompt user for y
    y = int(input("y: "))
    
    # Perform addition
    print(x + y)
```

Notice how the input for `x` and `y` is passed to the `int` function, which converts it to an integer. Without converting `x` and `y` to be integers, the characters will concatenate.