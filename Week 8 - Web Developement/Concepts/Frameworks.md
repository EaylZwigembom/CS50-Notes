
Similar to third-party libraries we can leverage in Python, there are third-party libraries called __frameworks__ that we can utilize with our HTML files.

__Bootstrap__ is one of these frameworks that we can use to beautify our HTML and easily perfect design elements such that our pages are more readable.

Bootstrap can be utilized by adding the following `link` tag in the `head` of your html file:
```
    <head>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
        <title>bootstrap</title>
    </head>
```

Consider the following HTML:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates table -->
    
    <html lang="en">
        <head>
            <title>phonebook</title>
        </head>
        <body>
            <table>
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Number</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carter</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>David</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>John</td>
                        <td>+1-949-468-2750</td>
                    </tr>
                </tbody>
            </table>
        </body>
    </html>
```

Notice how, when looking at a served version of this page, it’s quite plain.

Now consider the following HTML that implements the use of Bootstrap:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates table with Bootstrap -->
    
    <html lang="en">
        <head>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
            <title>phonebook</title>
        </head>
        <body>
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">Name</th>
                        <th scope="col">Number</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carter</td>
                        <td>+1-617-495-1000</td>
                    </tr>
                    <tr>
                        <td>David</td>
                        <td>+1-949-468-2750</td>
                    </tr>
                </tbody>
            </table>
        </body>
    </html>
```

Notice how much prettier this website is now.

Similarly, consider the following expansion of our search page created earlier:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates layout with Bootstrap -->
    
    <html lang="en">
        <head>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
            <title>search</title>
        </head>
        <body>
    
            <div class="container-fluid">
    
                <ul class="m-3 nav">
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://about.google/">About</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://store.google.com/">Store</a>
                    </li>
                    <li class="nav-item ms-auto">
                        <a class="nav-link text-dark" href="https://www.google.com/gmail/">Gmail</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://www.google.com/imghp">Images</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-dark" href="https://www.google.com/intl/en/about/products">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-grid-3x3-gap-fill" viewBox="0 0 16 16">
                                <path d="M1 2a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2zM1 7a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V7zM1 12a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2z"/>
                            </svg>
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="btn btn-primary" href="https://accounts.google.com/ServiceLogin" role="button">Sign in</a>
                    </li>
                </ul>
    
                <div class="text-center">
    
                    <!-- https://knowyourmeme.com/memes/happy-cat -->
                    <img alt="Happy Cat" class="img-fluid w-25" src="cat.gif">
    
                    <form action="https://www.google.com/search" class="mt-4" method="get">
                        <input autocomplete="off" autofocus class="form-control form-control-lg mb-4 mx-auto w-50" name="q" placeholder="Query" type="search">
                        <button class="btn btn-light">Google Search</button>
                        <button class="btn btn-light" name="btnI">I'm Feeling Lucky</button>
                    </form>
    
                </div>
    
            </div>
    
        </body>
    </html>
```

This version of the page is exceedingly stylized, thanks to Bootstrap.

You can learn more about this in the [Bootstrap Documentation](https://getbootstrap.com/docs/)