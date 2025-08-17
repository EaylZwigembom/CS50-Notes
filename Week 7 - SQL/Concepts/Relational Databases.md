
Google, X, and Meta all use relational databases to store their information at scale.

Relational databases store data in rows and columns in structures called __tables__.

SQL allows for four types of commands:
```
      Create
      Read
      Update
      Delete
```

These four operations are affectionately called __CRUD__.

We can create a database with the SQL syntax `CREATE TABLE table (column type, ...);`. But where do you run this command?

`sqlite3` is a type of SQL database that has the core features required for this course.

We can create a SQL database at the terminal by typing `sqlite3 favorites.db`. Upon being prompted, we will agree that we want to create `favorites.db` by pressing `y`.

You will notice a different prompt as we are now using a program called `sqlite`.

We can put `sqlite` into `csv` mode by typing `.mode csv`. Then, we can import our data from our `csv` file by typing `.import favorites.csv favorites`. It seems that nothing has happened!

We can type `.schema` to see the structure of the database.

You can read items from a table using the syntax `SELECT columns FROM table`.

For example, you can type `SELECT * FROM favorites;` which will print every row in `favorites`.

You can get a subset of the data using the command `SELECT language FROM favorites;`.

SQL supports many commands to access data, including: 
```   SQL
      AVG
      COUNT
      DISTINCT
      LOWER
      MAX
      MIN
      UPPER
```

For example, you can type `SELECT COUNT(*) FROM favorites;`. Further, you can type `SELECT DISTINCT language FROM favorites;` to get a list of the individual languages within the database. You could even type `SELECT COUNT(DISTINCT language) FROM favorites;` to get a count of those.

SQL offers additional commands we can utilize in our queries:
```
      WHERE       -- adding a Boolean expression to filter our data
      LIKE        -- filtering responses more loosely
      ORDER BY    -- ordering responses
      LIMIT       -- limiting the number of responses
      GROUP BY    -- grouping responses together
```

Notice that we use `--` to write a comment in SQL.