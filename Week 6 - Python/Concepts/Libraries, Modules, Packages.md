#python

As with C, the CS50 library can be utilized within Python.

The following functions will be of particular use:
```
get_float
get_int
get_string
```

You can import the cs50 library as follows:
```
import cs50
```

You also have the option of importing only specific functions from the CS50 library as follows:
```
from cs50 import get_float, get_int, get_string
```

If you want to use all of the functions then you can do the following:
```
import cs50

n = cs50.get_int("n: ")
fl = cs50.get_float("fl: ")
str = cs50.get_string("str: ")
```

Notice that in order to access functions from the CS50 library you have to first write the **name of the library**, then **`.`** the **name of the function** you want to access. That happens because you didn't specify what functions you are going to use and python doesn't want to fill your code with unused functions.

You can also give aliases for functions:
```
import cs50 as cs

n = cs.get_int("n: ")
fl = cs.get_float("fl: ")
str = cs.get_string("str: ")
```

Notice that to give the alias you have to add the **`as`** keyword after the library name, and only then you can give the alias to the function.

