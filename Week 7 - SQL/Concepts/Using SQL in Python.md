To assist in working with SQL in this course, the CS50 Library can be utilized as follows in your code:
```
    from cs50 import SQL
```

Similar to previous uses of the CS50 Library, this library will assist with the complicated steps of utilizing SQL within your Python code.

You can read more about the CS50 Library’s SQL functionality in the [documentation](https://cs50.readthedocs.io/libraries/cs50/python/#cs50.SQL).

Using our new knowledge of SQL, we can now leverage Python alongside.

Modify your code for `favorites.py` as follows:
```
    # Searches database popularity of a problem
    
    from cs50 import SQL
    
    # Open database
    db = SQL("sqlite:///favorites.db")
    
    # Prompt user for favorite
    favorite = input("Favorite: ")
    
    # Search for title
    rows = db.execute("SELECT COUNT(*) AS n FROM favorites WHERE language = ?", favorite)
    
    # Get first (and only) row
    row = rows[0]
    
    # Print popularity
    print(row["n"])
```

Notice that `db = SQL("sqlite:///favorites.db")` provides Python the location of the database file. Then, the line that begins with `rows` executes SQL commands utilizing `db.execute`. Indeed, this command passes the syntax within the quotation marks to the `db.execute` function. We can issue any SQL command using this syntax. Further, notice that `rows` is returned as a list of dictionaries. In this case, there is only one result, one row, returned to the rows list as a dictionary.