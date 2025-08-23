Moving on to a final example of utilizing Flask’s ability to enable a session.

We examined the following code for `store` in `app.py`. The following code was shown:
```
    from cs50 import SQL
    from flask import Flask, redirect, render_template, request, session
    from flask_session import Session
    
    # Configure app
    app = Flask(__name__)
    
    # Connect to database
    db = SQL("sqlite:///store.db")
    
    # Configure session
    app.config["SESSION_PERMANENT"] = False
    app.config["SESSION_TYPE"] = "filesystem"
    Session(app)
    
    
    @app.route("/")
    def index():
        books = db.execute("SELECT * FROM books")
        return render_template("books.html", books=books)
    
    
    @app.route("/cart", methods=["GET", "POST"])
    def cart():
    
        # Ensure cart exists
        if "cart" not in session:
            session["cart"] = []
    
        # POST
        if request.method == "POST":
            book_id = request.form.get("id")
            if book_id:
                session["cart"].append(book_id)
            return redirect("/cart")
    
        # GET
        books = db.execute("SELECT * FROM books WHERE id IN (?)", session["cart"])
        return render_template("cart.html", books=books)
```

Notice that `cart` is implemented using a list. Items can be added to this list using the `Add to Cart` buttons in `books.html`. When clicking such a button, the `post` method is invoked, where the `id` of the item is appended to the `cart`. When viewing the cart, invoking the `get` method, SQL is executed to display a list of the books in the cart.

We also saw the contents of `books.html`:
```
    {% extends "layout.html" %}
    
    {% block body %}
    
        <h1>Books</h1>
        {% for book in books %}
            <h2>{{ book["title"] }}</h2>
            <form action="/cart" method="post">
                <input name="id" type="hidden" value="{{ book['id'] }}">
                <button type="submit">Add to Cart</button>
            </form>
        {% endfor %}
    
    {% endblock %}
```

Notice how this creates the ability to `Add to Cart` for each book using `for book in books`.

You can see the rest of the files that power this `flask` implementation in the [source code](https://cdn.cs50.net/2024/fall/lectures/9/src9/store/).