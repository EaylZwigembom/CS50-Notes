We looked at a pre-designed program called `shows`, in `app.py`:
```
    # Searches for shows using LIKE
    
    from cs50 import SQL
    from flask import Flask, render_template, request
    
    app = Flask(__name__)
    
    db = SQL("sqlite:///shows.db")
    
    
    @app.route("/")
    def index():
        return render_template("index.html")
    
    
    @app.route("/search")
    def search():
        shows = db.execute("SELECT * FROM shows WHERE title LIKE ?", "%" + request.args.get("q") + "%")
        return render_template("search.html", shows=shows)
```

Notice how the `search` route allows for a way by which to search for a `show`. This search looks for titles `LIKE` the one provided by the user.

We also examined `index.html`:
```
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <meta name="viewport" content="initial-scale=1, width=device-width">
            <title>shows</title>
        </head>
    
        <body>
    
            <input autocomplete="off" autofocus placeholder="Query" type="text">
    
            <ul></ul>
    
            <script>
                let input = document.querySelector('input');
                input.addEventListener('input', async function() {
                    let response = await fetch('/search?q=' + input.value);
                    let shows = await response.json();
                    let html = '';
                    for (let id in shows) {
                        let title = shows[id].title.replace('<', '&lt;').replace('&', '&amp;');
                        html += '<li>' + title + '</li>';
                    }
                    document.querySelector('ul').innerHTML = html;
                });
            </script>
    
        </body>
    
    </html>
```

Notice that the JavaScript `script` creates an implementation of autocomplete, where titles that match the `input` are displayed.

You can see the rest of the files of this implementation in the [source code](https://cdn.cs50.net/2024/fall/lectures/9/src9/shows3/).