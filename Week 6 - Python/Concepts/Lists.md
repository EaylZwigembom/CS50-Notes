#python

`list`s are a data structure within Python.
`list`s have built-in methods or functions within them.
For example, consider the following code:
```
    # Averages three numbers using a list
    
    # Scores
    scores = [72, 73, 33]
    
    # Print average
    average = sum(scores) / len(scores)
    print(f"Average: {average}")
```

Notice that you can use the built-in `sum` method to calculate the average.

You can even utilize the following syntax to get values from the user:
```
    # Averages three numbers using a list and a loop
    
    from cs50 import get_int
    
    # Get scores
    scores = []
    for i in range(3):
        score = get_int("Score: ")
        scores.append(score)
    
    # Print average
    average = sum(scores) / len(scores)
    print(f"Average: {average}")
```

Notice that this code utilizes the built-in `append` method for lists.
 
You can learn more about lists in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

You can also learn more about `len` in the 
[Python documentation](https://docs.python.org/3/library/functions.html#len)