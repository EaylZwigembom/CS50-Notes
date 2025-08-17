While relational databases have the ability to be faster and more robust than utilizing a `CSV` file, data can be optimized within a table using __indexes__.

Indexes can be utilized to speed up our queries.

We can track the speed of our queries by executing `.timer on` in `sqlite3`.

To understand how indexes can speed up our queries, run the following: `SELECT * FROM shows WHERE title = 'The Office';` Notice the time that displays after the query executes.

Then, we can create an index with the syntax `CREATE INDEX title_index ON shows (title);`. This tells `sqlite3` to create an index and perform some special under-the-hood optimization relating to this column `title`.

This will create a data structure called a __B Tree__, a data structure that looks similar to a binary tree. However, unlike a binary tree, there can be more than two child nodes.
![one node at the top from which come four children and below that there are three children coming from one of the nodes and two from another two from another and three from another](https://cs50.harvard.edu/x/notes/7/cs50Week7Slide039.png "b tree")

Further, we can create indexes as follows:

```
    CREATE INDEX name_index ON people (name);
    CREATE INDEX person_index ON stars (person_id);
```

Running the query and you will notice that the query runs much more quickly!
```
    SELECT title FROM shows WHERE id IN 
        (SELECT show_id FROM stars WHERE person_id = 
            (SELECT id FROM people WHERE name = 'Steve Carell'));
```

Unfortunately, indexing all columns would result in utilizing more storage space. Therefore, there is a tradeoff for enhanced speed.