
Improving upon our program, we know that most users will not type arguments into the address bar. Instead, programmers rely upon users to fill out forms on web pages. Accordingly, we can modify `index.html` as follows:
```
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <meta name="viewport" content="initial-scale=1, width=device-width">
            <title>hello</title>
        </head>
    
        <body>
            <form action="/greet" method="get">
                <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
                <button type="submit">Greet</button>
            </form>
        </body>
    
    </html>
```

Notice that a form is now created that takes the user’s name and then passes it off to a route called `/greet`. `autocomplete` is turned off. Further, a `placeholder` with the text `name` is included. Further, notice how the `meta` tag is used to make the web page mobile-responsive.

Further, we can change `app.py` as follows:
```
    # Adds a form, second route
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/")
    def index():
        return render_template("index.html")
    
    
    @app.route("/greet")
    def greet():
        return render_template("greet.html", name=request.args.get("name", "world"))
```

Notice that the default path will display a form for the user to input their name. The `/greet` route will pass the `name` to that web page.

To finalize this implementation, you will need another template for `greet.html` in the `templates` folder as follows:
```
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <meta name="viewport" content="initial-scale=1, width=device-width">
            <title>hello</title>
        </head>
    
        <body>
            hello, {{ name }}
        </body>
    
    </html>
```

Notice that this route will now render the greeting to the user, followed by their name.