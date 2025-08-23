#python

It’s possible to have certain types of values not only have properties or attributes inside of them but have functions as well. In Python, these values are known as __objects__

In C, we could create a [[Structs|struct]] where you could associate multiple variables inside a single self-created data type. In Python, we can do this and also include functions in a self-created data type. When a function belongs to a specific __object__, it is known as a __method__.
 
For example, `strs` in Python have built-in __methods__. Therefore, you could modify your code as follows:
```
    # Logical operators, using lists
    
    # Prompt user to agree
    s = input("Do you agree? ").lower()
    
    # Check whether agreed
    if s in ["y", "yes"]:
        print("Agreed.")
    elif s in ["n", "no"]:
        print("Not agreed.")
```

Notice how the old value of `s` is overwritten with the result of `s.lower()`, a built-in method of `strs`.

Similarly, you may recall how we [[Memory#^copying-and-malloc|copied a string]] in C:
```
    // Capitalizes a copy of a string without memory errors
    
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    int main(void)
    {
        // Get a string
        char *s = get_string("s: ");
        if (s == NULL)
        {
            return 1;
        }
    
        // Allocate memory for another string
        char *t = malloc(strlen(s) + 1);
        if (t == NULL)
        {
            return 1;
        }
    
        // Copy string into memory
        strcpy(t, s);
    
        // Capitalize copy
        if (strlen(t) > 0)
        {
            t[0] = toupper(t[0]);
        }
    
        // Print strings
        printf("s: %s\n", s);
        printf("t: %s\n", t);
    
        // Free memory
        free(t);
        return 0;
    }
```

Notice the number of lines of code.

We may implement the above in Python as follows:
```
    # Capitalizes a copy of a string
    
    # Get a string
    s = input("s: ")
    
    # Capitalize copy of string
    t = s.capitalize()
    
    # Print strings
    print(f"s: {s}")
    print(f"t: {t}")
```

Notice how much shorter this program is than its counterpart in C.

In this class, we will only scratch the surface of Python. Therefore, the [Python documentation](https://docs.python.org/) will be of particular importance as you continue.

You can learn more about string methods in the 
[Python documentation](https://docs.python.org/3/library/stdtypes.html#string-methods)