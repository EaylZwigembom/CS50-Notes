#python

Recall that in C, we experienced truncation where one integer is divided by another could result in an imprecise result.

You can see how Python handles such division as follows by modifying your code for `calculator.py`:

```
    # Division with integers, demonstration lack of truncation
    
    # Prompt user for x
    x = int(input("x: "))
    
    # Prompt user for y
    y = int(input("y: "))
    
    # Divide x by y
    z = x / y
    print(z)
```

Notice that executing this code results in a value, but that if you were to see more digits after `.333333` you’d see that we are faced with __floating-point imprecision__. Truncation does not occur.

We can reveal this imprecision by modifying our codes slightly:
```
    # Floating-point imprecision
    
    # Prompt user for x
    x = int(input("x: "))
    
    # Prompt user for y
    y = int(input("y: "))
    
    # Divide x by y
    z = x / y
    print(f"{z:.50f}")
```

Notice that this code reveals the imprecision. Python still faces this issue, just as C does.