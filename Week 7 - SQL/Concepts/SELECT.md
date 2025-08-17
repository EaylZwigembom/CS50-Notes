
For example, we can execute `SELECT COUNT(*) FROM favorites WHERE language = 'C';`. A count is presented.

Further, we could type `SELECT COUNT(*) FROM favorites WHERE language = 'C' AND problem = 'Hello, World';`. Notice how the `AND` is utilized to narrow our results.

Similarly, we could execute `SELECT language, COUNT(*) FROM favorites GROUP BY language;`. This would offer a temporary table that would show the language and count.

We could improve this by typing `SELECT language, COUNT(*) FROM favorites GROUP BY language ORDER BY COUNT(*);`. This will order the resulting table by the `count`.

Likewise, we could execute `SELECT COUNT(*) FROM favorites WHERE language = 'C' AND (problem = 'Hello, World' OR problem = 'Hello, It''s Me');`. Do notice that there are two `''` marks as to allow the use of single quotes in a way that does not confuse SQL.

Further, we could execute `SELECT COUNT(*) FROM favorites WHERE language = 'C' AND problem LIKE 'Hello, %';` to find any problems that start with `Hello,` (including a space).

We can also group the values of each language by executing `SELECT language, COUNT(*) FROM favorites GROUP BY language;`.

We can order the output as follows: `SELECT language, COUNT(*) FROM favorites GROUP BY language ORDER BY COUNT(*) DESC;`.

We can even create aliases, like variables in our queries: `SELECT language, COUNT(*) AS n FROM favorites GROUP BY language ORDER BY n DESC;`.

Finally, we can limit our output to 1 or more values: `SELECT language, COUNT(*) AS n FROM favorites GROUP BY language ORDER BY n DESC LIMIT 1;`.