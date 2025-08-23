Frosh IMs or __froshims__ is a web application that allows students to register for intramural sports.

Close all your `hello` related windows and create a folder by typing `mkdir froshims` in the terminal window. Then, type `cd froshims` to browse to this folder. Within, create a directory called templates by typing `mkdir templates`.

Next, in the `froshims` folder, type `code requirements.txt` and code as follows:
```
    Flask
```

As before, Flask is required to run a Flask application.

Finally, type `code app.py` and write code as follows:
```
    # Implements a registration form using a select menu, validating sport server-side
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    SPORTS = [
        "Basketball",
        "Soccer",
        "Ultimate Frisbee"
    ]
    
    
    @app.route("/")
    def index():
        return render_template("index.html", sports=SPORTS)
    
    
    @app.route("/register", methods=["POST"])
    def register():
    
        # Validate submission
        if not request.form.get("name") or request.form.get("sport") not in SPORTS:
            return render_template("failure.html")
    
        # Confirm registration
        return render_template("success.html")
```

Notice that a `failure` option is provided, such that a failure message will be displayed to the user if the `name` or `sport` field is not properly filled out.

Next, create a file in the `templates` folder called `index.html` by typing `code templates/index.html` and write code as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
        <h1>Register</h1>
        <form action="/register" method="post">
            <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
            <select name="sport">
                <option disabled selected value="">Sport</option>
                {% for sport in sports %}
                    <option value="{{ sport }}">{{ sport }}</option>
                {% endfor %}
            </select>
            <button type="submit">Register</button>
        </form>
    {% endblock %}
```

Next, create a file called `layout.html` by typing `code templates/layout.html` and write code as follows:
```
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <meta name="viewport" content="initial-scale=1, width=device-width">
            <title>froshims</title>
        </head>
    
        <body>
            {% block body %}{% endblock %}
        </body>
    
    </html>
```

Fourth, create a file in templates called `success.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
        You are registered!
    {% endblock %}
```

Finally, create a file in templates called `failure.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
        You are not registered!
    {% endblock %}
```

Execute `flask run` and check out the application at this stage.

You can imagine how we might want to see the various registration options using radio buttons. We can improve `index.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
        <h1>Register</h1>
        <form action="/register" method="post">
            <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
            {% for sport in sports %}
                <input name="sport" type="radio" value="{{ sport }}"> {{ sport }}
            {% endfor %}
            <button type="submit">Register</button>
        </form>
    {% endblock %}
```

Notice how `type` has been changed to `radio`.

Again, executing `flask run` you can see how the interface has now changed.

You can imagine how we might want to accept the registration of many different registrants. We can improve `app.py` as follows:
```
    # Implements a registration form, storing registrants in a dictionary, with error messages
    
    from flask import Flask, redirect, render_template, request
    
    app = Flask(__name__)
    
    REGISTRANTS = {}
    
    SPORTS = [
        "Basketball",
        "Soccer",
        "Ultimate Frisbee"
    ]
    
    
    @app.route("/")
    def index():
        return render_template("index.html", sports=SPORTS)
    
    
    @app.route("/register", methods=["POST"])
    def register():
    
        # Validate name
        name = request.form.get("name")
        if not name:
            return render_template("error.html", message="Missing name")
    
        # Validate sport
        sport = request.form.get("sport")
        if not sport:
            return render_template("error.html", message="Missing sport")
        if sport not in SPORTS:
            return render_template("error.html", message="Invalid sport")
    
        # Remember registrant
        REGISTRANTS[name] = sport
    
        # Confirm registration
        return redirect("/registrants")
    
    
    @app.route("/registrants")
    def registrants():
        return render_template("registrants.html", registrants=REGISTRANTS)
```

Notice that a dictionary called `REGISTRANTS` is used to log the `sport` selected by `REGISTRANTS[name]`. Also, notice that `registrants=REGISTRANTS` passes the dictionary on to this template.

Additionally, we can implement `error.html`:
```
    {% extends "layout.html" %}
    
    {% block body %}
        <h1>Error</h1>
        <p>{{ message }}</p>
        <img alt="Grumpy Cat" src="/static/cat.jpg">
    {% endblock %}
```

Further, create a new template called `registrants.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
        <h1>Registrants</h1>
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Sport</th>
                </tr>
            </thead>
            <tbody>
                {% for name in registrants %}
                    <tr>
                        <td>{{ name }}</td>
                        <td>{{ registrants[name] }}</td>
                    </tr>
                {% endfor %}
            </tbody>
        </table>
    {% endblock %}
```

Notice that `{% for name in registrants %}...{% endfor %}` will iterate through each of the registrants. Very powerful to be able to iterate on a dynamic web page!

Finally, create a folder called `static` in the same folder as `app.py`. There, upload the following file of a [cat](https://cdn.cs50.net/2024/fall/lectures/9/src9/froshims4/static/cat.jpg).

Execute `flask run` and play with the application.
 
You now have a web application! However, there are some security flaws! Because everything is client-side, an adversary could change the HTML and __hack__ a website. Further, this data will not persist if the server is shut down. Could there be some way we could have our data persist even when the server restarts?