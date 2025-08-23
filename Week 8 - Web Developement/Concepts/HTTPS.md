__HTTP__ or _hypertext transfer protocol_ is an application-level protocol that developers use to build powerful and useful things through the transfer of data from one place to another. __HTTPS__ is a secure version of this protocol.

When you see an address such as `https://www.example.com` you are actually implicitly visiting that address with a `/` at the end of it.

The _path_ is what exists after that slash. For example, `https://www.example.com/folder/file.html` visits `example.com` and browses to the `folder` directory, and then visits the file named `file.html`.

The `.com` is called a _top-level domain_ that is used to denote the location or type of organization associated with this address.

`https` in this address is the protocol that is used to connect to that web address. By protocol, we mean that HTTP utilizes `GET` or `POST` __requests__ to ask for information from a server. For example, you can launch Google Chrome, right-click, and click `inspect`. When you open the `developer tools` and visit `Network`, selecting `Preserve log`, you will see `Request Headers`. You’ll see mentions of `GET`. This is possible in other browsers as well, using slightly different methods.

For example, when issuing a GET request, your computer may send the following to a server:

 ```
    GET / HTTP/2
    Host: www.harvard.edu
```

Notice that this requests via HTTP the content served on www.harvard.edu.

Generally, after making a request to a server, you will receive the following in `Response Headers`:

```
    HTTP/2 200
    Content-Type: text/html
```

This approach to inspecting these logs may be a bit more complicated than need be. You can analyze the work of HTTP protocols at [cs50.dev](https://cs50.dev/). For example, type the following in your terminal window:

```
    curl -I https://www.harvard.edu/
```

Notice that the output of this command returns all the header values of the responses of the server.

Via developer tools in your web browser, you can see all the HTTP requests when browsing to the above website.

Further, execute the following command in your terminal window:

```
    curl -I https://harvard.edu
```

Notice that you will see a `301` response, providing a hint to a browser of where it can find the correct website.

Similarly, execute the following in your terminal window:

```
    curl -I http://www.harvard.edu/
```

Notice that the `s` in `https` has been removed. The server response will show that the response is `301`, meaning that the website has permanently moved.

Similar to `301`, a code of `404` means that a specified URL has not been found. There are numerous other response codes, such as:

```
    200 OK
    301 Moved Permanently
    302 Found
    304 Not Modified
    307 Temporary Redirect
    401 Unauthorized
    403 Forbidden
    404 Not Found
    418 I'm a Teapot
    500 Internal Server Error
    503 Service Unavailable
```

It’s worth mentioning that `500` errors are always your fault as the developer when they concern a product or application of your creation. This will be especially important for next week’s problem set, and potentially for your final project!