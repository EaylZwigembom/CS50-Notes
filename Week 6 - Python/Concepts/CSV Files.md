#python

Python also has built-in support for CSV files.
Modify your code for `phonebook.py` as follows:
```
    import csv
    
    file = open("phonebook.csv", "a")
    
    name = input("Name: ")
    number = input("Number: ")
    
    writer = csv.writer(file)
    writer.writerow([name,number])
    
    file.close()
```

Notice `writerow` adds the commas in the CSV file for us.

While `file.close` and `file = open` are commonly used and available syntax in Python, this code can be improved as follows:
```
    import csv
    
    name = input("Name: ")
    number = input("Number: ")
    
    with open("phonebook.csv", "a") as file:
    
        writer = csv.writer(file)
        writer.writerow([name,number])
```

Notice that the code is indented under the `with` statement. This automatically closes the file when done.

Similarly, we can write a dictionary as follows within the CSV file:
```
    import csv
    
    name = input("Name: ")
    number = input("Number: ")
    
    with open("phonebook.csv", "a") as file:
    
        writer = csv.DictWriter(file, fieldnames=["name", "number"])
        writer.writerow({"name": name, "number": number})
```

Notice this code is quite similar to our prior iteration but with `csv.DictWriter` instead.

Notice how much simpler it is than [[Memory#^file-i-o|FILE I/O in C]]