#python

We can also search within a data structure.

Consider a program called `phonebook.py` as follows: 
```
    # Implements linear search for names using loop
    
    # A list of names
    names = ["Yuliia", "David", "John"]
    
    # Ask for name
    name = input("Name: ")
    
    # Search for name
    for n in names:
        if name == n:
            print("Found")
            break
    else:
        print("Not found")
```

Notice how this implements linear search for each name.

However, we don’t need to iterate through a list. In Python, we can execute linear search as follows:
```
    # Implements linear search for names using `in`
    
    # A list of names
    names = ["Yuliia", "David", "John"]
    
    # Ask for name
    name = input("Name: ")
    
    # Search for name
    if name in names:
        print("Found")
    else:
        print("Not found")
```

Notice how `in` is used to implement linear search.
Still, this code could be improved.

Recall that a _dictionary_ or `dict` is a collection of __key__ and __value__ pairs.

You can implement a dictionary in Python as follows: 
```
    # Implements a phone book as a list of dictionaries, without a variable
    
    from cs50 import get_string
    
    people = [
        {"name": "Yuliia", "number": "+1-617-495-1000"},
        {"name": "David", "number": "+1-617-495-1000"},
        {"name": "John", "number": "+1-949-468-2750"},
    ]
    
    # Search for name
    name = get_string("Name: ")
    for person in people:
        if person["name"] == name:
            print(f"Found {person['number']}")
            break
    else:
        print("Not found")
```

Notice that the dictionary is implemented having both `name` and `number` for each entry.

Even better, strictly speaking, we don’t need both a `name` and a `number`. We can simplify this code as follows:
```
    # Implements a phone book using a dictionary
    
    from cs50 import get_string
    
    people = {
        "Yuliia": "+1-617-495-1000",
        "David": "+1-617-495-1000",
        "John": "+1-949-468-2750",
    }
    
    # Search for name
    name = get_string("Name: ")
    if name in people:
        print(f"Number: {people[name]}")
    else:
        print("Not found")
```

Notice that the dictionary is implemented using curly braces. Then, the statement `if name in people` searches to see if the `name` is in the `people` dictionary. Further, notice how, in the `print` statement, we can index into the people dictionary using the value of `name`. Very useful!

Python has done their best to get to __constant time__ using their built-in searches.

You can learn more about dictionaries in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#dict)