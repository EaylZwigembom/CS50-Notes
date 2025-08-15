#python

Functions in C like `fread`, `fwrite`, and `printf` use positional arguments, where you provide arguments with commas as separators. You, the programmer, must remember what argument is in which position. These are referred to as __positional arguments__.

In Python, __named parameters__ allow you to provide arguments without regard to positionality(place/order of the parameters).

You can learn more about the parameters of the `print` function in the [documentation](https://docs.python.org/3/library/functions.html#print).

Accessing that documentation, you may see the following:
```
print(*objects, sep=' ', end='\n', file=None, flush=False)
```

Notice that various objects can be provided to print. A separator of a single space is provided that will display when more than one object is given to `print`. Similarly, a new line is provided at the end of the `print` statement.