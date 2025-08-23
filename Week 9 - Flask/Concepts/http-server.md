Up until this point, all HTML you saw was pre-written and static.

In the past, when you visited a page, the browser downloaded an HTML page, and you were able to view it. These are considered __static__ pages, in that what is programmed in the HTML is exactly what the user sees and downloads __client-side__ to their internet browser.

Dynamic pages refer to the ability of [[Hello Python!|Python]] and similar languages to create HTML on-the-fly. Accordingly, you can have web pages that are generated __server-side__ by code based upon the input or behavior of users.

You have used `http-server` in the past to serve your web pages. Today, we are going to utilize a new server that can parse out a web address and perform actions based on the URL provided.

Further, last week, you saw URLs as follows:
 ```
 https://www.example.com/folder/file.html
```

Notice that `file.html` is an HTML file inside a folder called `folder` at `example.com`.