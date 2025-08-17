Now, still considering the code above, you might be wondering what the `?` question marks do above. One of the problems that can arise in real-world applications of SQL is what is called an _injection attack_. An injection attack is where a malicious actor could input malicious SQL code.

For example, consider a login screen as follows:
![harvard key login screen with username and password fields](https://cs50.harvard.edu/x/notes/7/cs50Week7Slide051.png "harvard key login screen")

Without the proper protections in our own code, a bad actor could run malicious code. Consider the following:
```
rows = db.execute("SELECT COUNT(*) FROM users WHERE username = ? AND password = ?", username, password)
```

Notice that because the `?` is in place, validation can be run on `favorite` before it is blindly accepted by the query.

You never want to utilize formatted strings in queries as above or blindly trust the user’s input.

because if they input some SQL code it might actually ruin the query. consider this following code:
```
rows = db.execute("SELECT COUNT(*) FROM users WHERE username = '{username}' AND password = '{password}'")
```

if the user will write in the email input for example: **`malan@harvard.edu'--`** it would make the user log in as David J Malan without even knowing his password. Consider this SQL query after the input of the user:
```
rows = db.execute("SELECT COUNT(*) FROM users WHERE username = 'malan@harvard.edu'--' AND password = '{password}'")
```
Now you see that after entering **`malan@harvard.edu'--`** in the email field, the query searches **only for the email** because the email prompt had **`'`** which basically closed the formatted string, and then **`--`** which turned whatever SQL code after that into a **comment**, which means that the part of the query that checked for the password is now a comment.

So after the prompt of the user this was the actual query:
```
rows = db.execute("SELECT COUNT(*) FROM users WHERE username = 'malan@harvard.edu'")
```

Utilizing the CS50 Library, the library will __sanitize__ and remove any potentially malicious characters.

Watch this video for better understanding of SQL injections