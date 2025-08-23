`CSS`, or __cascading style sheet__, is a markup language that allows you to fine-tune the aesthetics of your HTML files.

CSS is filled with __properties__, which include key-value pairs.

In your terminal, type `code home.html` and write code as follows:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates inline CSS with P tags -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body>
            <p style="font-size: large; text-align: center;">
                John Harvard
            </p>
            <p style="font-size: medium; text-align: center;">
                Welcome to my home page!
            </p>
            <p style="font-size: small; text-align: center;">
                Copyright &#169; John Harvard
            </p>
        </body>
    </html>
```

Notice that some `style` attributes are provided to the `<p>` tags. The `font-size` is set to `large`, `medium`, or `small`. Then `text-align` is set to center.

While correct, the above is not well-designed. We can remove redundancy by modifying our code as follows:
```
    <!DOCTYPE html>
    
    <!-- Removes outer DIV -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body style="text-align: center">
            <div style="font-size: large">
                John Harvard
            </div>
            <div style="font-size: medium">
                Welcome to my home page!
            </div>
            <div style="font-size: small">
                Copyright &#169; John Harvard
            </div>
        </body>
    </html>
```

Notice that `<div>` tags are used to divide up this HTML file into specific regions. `text-align: center` is invoked on the entire body of the HTML. Because everything inside `body` is a child of `body`, the `center` attribute cascades down to those children.

It turns out that there are newer semantic tags included in HTML. We can modify our code as follows:
```
    <!DOCTYPE html>
    
    <!-- Uses semantic tags instead of DIVs -->
    
    <html lang="en">
        <head>
            <title>css</title>
        </head>
        <body style="text-align: center">
            <header style="font-size: large">
                John Harvard
            </header>
            <main style="font-size: medium">
                Welcome to my home page!
            </main>
            <footer style="font-size: small">
                Copyright &#169; John Harvard
            </footer>
        </body>
    </html>
```

Notice that the `header` and `footer` both have different styles assigned to them.

This practice of placing the style and information all in the same location is not good practice. We could move the elements of style to the top of the file as follows:
```
    <!-- Demonstrates class selectors -->
    
    <html lang="en">
        <head>
            <style>
    
                .centered
                {
                    text-align: center;
                }
    
                .large
                {
                    font-size: large;
                }
    
                .medium
                {
                    font-size: medium;
                }
    
                .small
                {
                    font-size: small;
                }
    
            </style>
            <title>css</title>
        </head>
        <body class="centered">
            <header class="large">
                John Harvard
            </header>
            <main class="medium">
                Welcome to my home page!
            </main>
            <footer class="small">
                Copyright &#169; John Harvard
            </footer>
        </body>
    </html>
```

Notice all the style tags are placed up in the `head` in the `style` tag wrapper. Also, notice that we’ve assigned __classes__, called `centered`, `large`, `medium`, and `small` to our elements, and that we select those classes by placing a dot before the name, as in `.centered`

It turns out that we can move all our style code into a special file called a __CSS__ file. We can create a file called `style.css` and paste our classes there:
```
    .centered
    {
        text-align: center;
    }
    
    .large
    {
        font-size: large;
    }
    
    .medium
    {
        font-size: medium;
    }
    
    .small
    {
        font-size: small;
    }
```

Notice that this is verbatim what appeared in our HTML file.

We then can tell the browser where to locate the CSS for this HTML file:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates external stylesheets -->
    
    <html lang="en">
        <head>
            <link href="style.css" rel="stylesheet">
            <title>css</title>
        </head>
        <body class="centered">
            <header class="large">
                John Harvard
            </header>
            <main class="medium">
                Welcome to my home page!
            </main>
            <footer class="small">
                Copyright &#169; John Harvard
            </footer>
        </body>
    </html>
 ```

Notice that `style.css` is linked to this HTML file as a stylesheet, telling the browser where to locate the styles we created.