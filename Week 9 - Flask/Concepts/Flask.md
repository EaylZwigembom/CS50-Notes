This week, we introduce the ability to engage with __routes__ such as `https://www.example.com/route?key=value`, where specific functionality can be generated on the server via the keys and values provided in the URL.

__Flask__ is a third-party library that allows you to host web applications using the Flask framework, or a micro-framework, within Python.

You can run Flask by executing `flask run` in your terminal window in [cs50.dev](https://cs50.dev/).

To do so, you will need a file called `app.py` and another called `requirements.txt`. `app.py` contains code the tells Flask how to run your web application. `requirements.txt` includes a list of the libraries that are required for your Flask application to run.

Here is a sample of `requirements.txt`:
```
Flask
```

Notice only `Flask` appears in this file. This is because Flask is required to run the Flask application.

Here is a very simple Flask application in `app.py`:
```
    # Says hello to world by returning a string of text
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/")
    def index():
        return "hello, world"
```

Notice that the `/` route simply returns the text `hello, world`.

We can also create code that implements HTML:
```
    # Says hello to world by returning a string of HTML
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/")
    def index():
        return '<!DOCTYPE html><html lang="en"><head><title>hello</title></head><body>hello, world</body></html>'
```

Notice that rather than returning simple text, this provides HTML.
 
Improving our application, we can also serve HTML based upon templates by creating a folder called `templates` and creating a file called `index.html` with the following code within that folder:
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
    
Notice the double `{{ name }}` that is a placeholder for something that will be later provided by our Flask server.

Then, in the same folder that the `templates` folder appears, create a file called `app.py` and add the following code:
```
    # Uses request.args.get
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/")
    def index():
        name = request.args.get("name", "world")
        return render_template("index.html", name=name)
```

Notice that this code defines `app` as the Flask application. Then, it defines the `/` route of `app` as returning the contents of `index.html` with the argument of `name`. By default, the `request.args.get` function will look for the `name` being provided by the user. If no name is provided, it will default to `world`. `@app.route` is otherwise known as a decorator.

You can run this web application by typing `flask run` in the terminal window. If Flask does not run, ensure that your syntax is correct in each of the files above. Further, if Flask will not run, make sure your files are organized as follows:
```
    /templates
        index.html
    app.py
    requirements.txt
```
    
Once you get it running, you will be prompted to click a link. Once you navigate to that webpage, try adding `?name=[Your Name]` to the base URL in your browser’s URL bar.