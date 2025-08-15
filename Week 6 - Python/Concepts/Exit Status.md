#python

The `sys` library also has built-in methods. We can use `sys.exit(i)` to exit the program with a specific exit code:

```
# Exits with explicit value, importing sys

import sys

if len(sys.argv) != 2:
    print("Missing command-line argument")
    sys.exit(1)

print(f"hello, {sys.argv[1]}")
sys.exit(0)
```

Notice that dot-notation is used to utilize the built-in functions of `sys`.