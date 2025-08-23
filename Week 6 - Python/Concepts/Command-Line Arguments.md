#python

As with C, you can also utilize [[Command Line Arguments|command-line arguments]]. Consider the following code:
```
# Prints a command-line argument
    
    from sys import argv
    
    if len(argv) == 2:
        print(f"hello, {argv[1]}")
    else:
        print("hello, world")
```

Notice that `argv[1]` is printed using a __formatted string__, noted by the `f` present in the `print` statement.

You can learn more about the `sys` library in the [Python documentation](https://docs.python.org/3/library/sys.html)