#python

Let’s explore more about exceptions that can occur when we run Python code.

Modify `calculator.py` as follows:
    
```
    # Doesn't handle exception
    
    # Prompt user for an integer
    n = int(input("Input: "))
    print("Integer")
```

Notice that inputting the wrong data could result in an error.

We can `try` to handle and __catch__ potential exceptions by modifying our code as follows:
```
# Handles exception
  
 # Prompt user for an integer
try:
    n = int(input("Input: "))
    print("Integer.")
except ValueError:
     print("Not integer.")
```

Notice that the above code repeatedly tries to get the correct type of data, providing additional prompts when needed.