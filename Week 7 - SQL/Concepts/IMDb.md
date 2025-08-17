We can imagine a database that we might want to create to catalog various TV shows. We could create a spreadsheet with columns like `title`, `star`, `star`, `star`, `star`, and more stars. A problem with this approach is that it has a lot of wasted space. Some shows may have one star. Others may have dozens.

We could separate our database into multiple sheets. We could have a `shows` sheet, a `stars` sheet, and a `people` sheet. On the `people` sheet, each person could have a unique `id`. On the `shows` sheet, each show could have a unique `id` too. On a third sheet called `stars` we could relate how each show has people for each show by having a `show_id` and `person_id`. While this is an improvement, this is not an ideal database.

IMDb offers a database of people, shows, writers, stars, genres, and ratings. Each of these tables is related to one another as follows:
![six boxes that represent various sql tables arrows are drawn to each showing their many relationships with one another](https://cs50.harvard.edu/x/notes/7/cs50Week7Slide025.png "imdb relationships")

After downloading [`shows.db`](https://cdn.cs50.net/2024/fall/lectures/7/src7/imdb/shows.db), you can execute `sqlite3 shows.db` in your terminal window.

Let’s zero in on the relationship between two tables within the database called `shows` and `ratings`. The relationship between these two tables can be illustrated as follows:
![two boxes one called shows and the other called ratings](https://cs50.harvard.edu/x/notes/7/cs50Week7Slide032.png "imdb shows and ratings")

To illustrate the relationship between these tables, we could execute the following command: `SELECT * FROM ratings LIMIT 10;`. Examining the output, we could execute `SELECT * FROM shows LIMIT 10;`.

Examining `shows` and `rating`, we can see these have a one-to-one relationship: One show has one rating.

To understand the database, upon executing `.schema` you will find not only each of the tables but the individual fields inside each of these fields.

More specifically, you could execute `.schema shows` to understand the fields inside `shows`. You can also execute `.schema ratings` to see the fields inside `ratings`.

As you can see, `show_id` exists in all of the tables. In the `shows` table, it is simply called `id`. This common field between all the fields is called a __key__. **Primary keys** are used to identify a unique record in a table. __Foreign keys__ are used to build relationships between tables by pointing to the primary key in another table. You can see in the schema of `ratings` that `show_id` is a foreign key that references `id` in `shows`.

By storing data in a relational database, as above, data can be more efficiently stored.

In __sqlite__, we have five data types, including:
```
      BLOB       -- binary large objects that are groups of ones and zeros
      INTEGER    -- an integer
      NUMERIC    -- for numbers that are formatted specially like dates
      REAL       -- like a float
      TEXT       -- for strings and the like
```

Additionally, columns can be set to add special constraints:
```
      NOT NULL
      UNIQUE
```

We can further play with this data to understand these relationships. Execute `SELECT * FROM ratings;`. There are a lot of ratings!

We can further limit this data down by executing `SELECT show_id FROM ratings WHERE rating >= 6.0 LIMIT 10;`. From this query, you can see that there are 10 shows presented. However, we don’t know what show each `show_id` represents.

You can discover what shows these are by executing `SELECT * FROM shows WHERE id = 626124;`

We can further our query to be more efficient by executing:
```
    SELECT title
    FROM shows
    WHERE id IN (
        SELECT show_id
        FROM ratings
        WHERE rating >= 6.0
        LIMIT 10
    )
```

Notice that this query nests together two queries. An inner query is used by an outer query.