
You can imagine scenarios where it is not safe to utilize `get`, as usernames and passwords would show up in the URL.

We can utilize the method `post` to help with this problem by modifying `app.py` as follows:
```
    # Switches to POST
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/")
    def index():
        return render_template("index.html")
    
    
    @app.route("/greet", methods=["POST"])
    def greet():
        return render_template("greet.html", name=request.form.get("name", "world"))
```

Notice that `POST` is added to the `/greet` route, and that we use `request.form.get` rather than `request.args.get`.

This tells the server to look __deeper__ into the virtual envelope and not reveal the items in `post` in the URL.

Still, this code can be advanced further by utilizing a single route for both `get` and `post`. To do this, modify `app.py` as follows:
```
    # Uses a single route
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/", methods=["GET", "POST"])
    def index():
        if request.method == "POST":
            return render_template("greet.html", name=request.form.get("name", "world"))
        return render_template("index.html")
```

Notice that both `get` and `post` are done in a single routing. However, `request.method` is utilized to properly route based on the type of routing requested by the user.

Accordingly, you can modify your `index.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
    
        <form action="/" method="post">
            <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
            <button type="submit">Greet</button>
        </form>
    
    {% endblock %}
```

Notice that the form `action` is changed.

Still, there is a bug still in this code. With our new implementation, when someone types in no name into the form, `Hello,` is displayed without a name. We can improve our code by editing `app.py` as follows:
```
    # Moves default value to template
    
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    
    @app.route("/", methods=["GET", "POST"])
    def index():
        if request.method == "POST":
            return render_template("greet.html", name=request.form.get("name"))
        return render_template("index.html")
```

Notice that `name=request.form.get("name"))` is changed.

Finally, change `greet.html` as follows:
```
    {% extends "layout.html" %}
    
    {% block body %}
    
        hello,
        {% if name %}
            {{ name }}
        {% else %}
            world
        {% endif %}
    
    {% endblock %}
```

Notice how `hello, {{ name }}` is changed to allow for a default output when no name is identified.

As we’ve been changing many files, you may wish to compare your final code with [our final code](https://cdn.cs50.net/2024/fall/lectures/9/src9/hello10/).