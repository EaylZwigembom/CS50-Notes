JavaScript is another programming language that allows for interactivity within web pages.

Consider the following implementation of `hello.html` that includes both JavaScript and HTML:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates onsubmit -->
    
    <html lang="en">
        <head>
            <script>
    
                function greet()
                {
                    alert('hello, ' + document.querySelector('#name').value);
                }
    
            </script>
            <title>hello</title>
        </head>
        <body>
            <form onsubmit="greet(); return false;">
                <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
                <input type="submit">
            </form>
        </body>
    </html>
```

Notice how this form uses an `onsubmit` property to trigger a `script` found at the top of the file. The script uses `alert` to create an alert pop-up. `#name.value` goes to the textbox on the page and obtains the value typed by the user.

Generally, it’s considered bad design to mix onsubmit and JavaScript. We can advance our code as follows:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates DOMContentLoaded -->
    
    <html lang="en">
        <head>
            <script>
    
                document.addEventListener('DOMContentLoaded', function() {
                    document.querySelector('form').addEventListener('submit', function(e) {
                        alert('hello, ' + document.querySelector('#name').value);
                        e.preventDefault();
                    });
                });
    
            </script>
            <title>hello</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
                <input type="submit">
            </form>
        </body>
    </html>
```

Notice that this version of the code creates an `addEventListener` to listen to the form `submit` being triggered. Notice how `DOMContentLoaded` ensures that the whole page is loaded before executing the JavaScript.

We can advance this code as follows:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates keyup and template literals -->
    
    <html lang="en">
        <head>
            <script>
    
                document.addEventListener('DOMContentLoaded', function() {
                    let input = document.querySelector('input');
                    input.addEventListener('keyup', function(event) {
                        let name = document.querySelector('p');
                        if (input.value) {
                            name.innerHTML = `hello, ${input.value}`;
                        }
                        else {
                            name.innerHTML = 'hello, whoever you are';
                        }
                    });
                });
    
            </script>
            <title>hello</title>
        </head>
        <body>
            <form>
                <input autocomplete="off" autofocus placeholder="Name" type="text">
            </form>
            <p></p>
        </body>
    </html>
```

Notice that the DOM is dynamically updated in memory as the user types out a name. If there is a value inside `input`, upon the `keyup` on the keyboard, the DOM is updated. Otherwise, default text is presented.

JavaScript allows you to dynamically read and modify the html document loaded into memory such that the user need not reload to see changes.

Consider the following HTML:
```
    <!DOCTYPE html>
    
    <!-- Demonstrates programmatic changes to style -->
    
    <html lang="en">
        <head>
            <title>background</title>
        </head>
        <body>
            <button id="red">R</button>
            <button id="green">G</button>
            <button id="blue">B</button>
            <script>
    
                let body = document.querySelector('body');
                document.querySelector('#red').addEventListener('click', function() {
                    body.style.backgroundColor = 'red';
                });
                document.querySelector('#green').addEventListener('click', function() {
                    body.style.backgroundColor = 'green';
                });
                document.querySelector('#blue').addEventListener('click', function() {
                    body.style.backgroundColor = 'blue';
                });
    
            </script>
        </body>
    </html>
```

Notice that JavaScript listens for when a specific button is clicked. Upon such a click, certain style attributes on the page are changed. `body` is defined as the body of the page. Then, an event listener waits for the clicking of one of the buttons. Then, the `body.style.backgroundColor` is changed.
    
Similarly, consider the following:
```
    <!DOCTYPE html>
    
    <html lang="en">
        <head>
            <script>
    
                // Toggles visibility of greeting
                function blink()
                {
                    let body = document.querySelector('body');
                    if (body.style.visibility == 'hidden')
                    {
                        body.style.visibility = 'visible';
                    }
                    else
                    {
                        body.style.visibility = 'hidden';
                    }
                }
    
                // Blink every 500ms
                window.setInterval(blink, 500);
    
            </script>
            <title>blink</title>
        </head>
        <body>
            hello, world
        </body>
    </html>
```

This example blinks a text at a set interval. Notice that `window.setInterval` takes in two arguments: A function to be called and a waiting period (in milliseconds) between function calls.

Consider the following implementation of JavaScript that autocompletes text:
```
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <title>autocomplete</title>
        </head>
    
        <body>
    
            <input autocomplete="off" autofocus placeholder="Query" type="text">
    
            <ul></ul>
    
            <script src="large.js"></script>
            <script>
          
                let input = document.querySelector('input');
                input.addEventListener('keyup', function(event) {
                    let html = '';
                    if (input.value) {
                        for (word of WORDS) {
                            if (word.startsWith(input.value)) {
                                html += `<li>${word}</li>`;
                            }
                        }
                    }
                    document.querySelector('ul').innerHTML = html;
                });
    
            </script>
    
        </body>
    </html>
```

This is a JavaScript implementation of autocomplete. This pulls from a file (not pictured here) called `large.js` that is a list of words.

The capabilities of JavaScript are many and can be found in the [JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript).