__Regular expressions__ or __regexes__ are a means by which to ensure that user-provided data fits a specific format.

We can implement our own registration page that utilizes regexes as follows:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates type="email" -->
    
    <html lang="en">
        <head>
            <title>register</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus name="email" placeholder="Email" type="email">
                <button>Register</button>
            </form>
        </body>
    </html>
```

Notice that the `input` tag includes attributes that designate that this is of type `email`. The browser knows to double-check that the input is an email address.

While the browser uses these built-in attributes to check for an email address, we can add a `pattern` attribute to 

ensure that only specific data ends up in the email address:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates pattern attribute -->
    
    <html lang="en">
        <head>
            <title>register</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus name="email" pattern=".+@.+\.edu" placeholder="Email" type="email">
                <button>Register</button>
            </form>
        </body>
    </html>
```

Notice that the `pattern` attribute is handed a regular expression to denote that the email address must include an `@` symbol and a `.edu`.

You can learn more about regular expressions from [Mozilla’s documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions). Further, you can make inquiries to [cs50.ai](https://cs50.ai/) for hints.