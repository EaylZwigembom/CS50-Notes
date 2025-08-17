Utilization of SQL can sometimes result in some problems.

You can imagine a case where multiple users could be accessing the same database and executing commands at the same time.

This could result in glitches where code is interrupted by other people’s actions. This could result in a loss of data.

Built-in SQL features such as `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` help avoid some of these race condition problems.

Watch [this video](https://youtu.be/ZA25WHO62ZA?t=8635
) to understand race condition better