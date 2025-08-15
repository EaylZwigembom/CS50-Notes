#python


Loops in Python are very similar to C. You may recall the following code in C:
```
    // Demonstrates for loop
    
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i < 3; i++)
        {
            printf("meow\n");
        }
    }
```
 
`for` loops can be implemented in Python as follows:
```
    # Better design
    
    for i in range(3):
        print("meow")
```

Notice that `i` is never explicitly used. However, Python will increment the value of `i`.

Further, a `while` loop could be implemented as follows:
```
    # Demonstrates while loop
    
    i = 0
    while i < 3:
        print("meow")
        i += 1
 ```

To further our understanding of loops and iteration in Python, let’s create a new file called `uppercase.py` as follows:
```
    # Uppercases string one character at a time
    
    before = input("Before: ")
    print("After:  ", end="")
    for c in before:
        print(c.upper(), end="")
    print()
```

Notice how `end=` is used to pass a parameter to the `print` function that continues the line without a line ending. This code passes one string at a time.

Reading the documentation, we discover that Python has methods that can be implemented upon the entire string as follows:
```
    # Uppercases string all at once
    
    before = input("Before: ")
    after = before.upper()
    print(f"After:  {after}")
```

Notice how `.upper` is applied to the entire string.