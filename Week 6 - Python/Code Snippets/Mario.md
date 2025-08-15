
#code-snippet #python 

Recall a few weeks ago our challenge of building three blocks on top of one another, like in Mario.
![three vertical blocks](https://cs50.harvard.edu/x/notes/6/cs50Week6Slide073.png "mario blocks")

In Python, we can implement something akin to this as follows:
```
    # Prints a column of 3 bricks with a loop
    
    for i in range(3):
        print("#")
```

This prints a column of three bricks.

In C, we had the advantage of a `do-while` loop. However, in Python, it is conventional to utilize a `while` loop, as Python does not have a `do-while` loop. You can write code as follows in a file called `mario.py`:
```
    # Prints a column of n bricks with a loop
    
    from cs50 import get_int
    
    while True:
        n = get_int("Height: ")
        if n > 0:
            break
    
    for i in range(n):
        print("#")
```

Notice how the while loop is used to obtain the height. Once a height greater than zero is inputted, the loop breaks.

Consider the following image:

![four horizontal question blocks](https://cs50.harvard.edu/x/notes/6/cs50Week6Slide075.png "mario blocks")

In Python, we could implement by modifying your code as follows:
```
    # Prints a row of 4 question marks with a loop
    
    for i in range(4):
        print("?", end="")
    print()
```

Notice that you can override the behavior of the `print` function to stay on the same line as the previous print.

Similar in spirit to previous iterations, we can further simplify this program:
```
    # Prints a row of 4 question marks without a loop
    
    print("?" * 4)
```

Notice that we can utilize `*` to multiply the print statement to repeat `4` times.

What about a large block of bricks?
![three by three block of mario blocks](https://cs50.harvard.edu/x/notes/6/cs50Week6Slide078.png "mario blocks")

To implement the above, you can modify your code as follows:
```
    # Prints a 3-by-3 grid of bricks with loops
    
    for i in range(3):
        for j in range(3):
            print("#", end="")
        print()
```

Notice how one `for` loop exists inside another. The `print` statement adds a new line at the end of each row of bricks.

You can learn more about the `print` function in the [Python documentation](https://docs.python.org/3/library/functions.html#print)