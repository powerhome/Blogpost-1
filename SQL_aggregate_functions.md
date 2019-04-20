# The Power of SQL Aggregate Functions

Throughout my first few months, there has been so many topics we had to cover from basic Ruby conditionals and iterations, to more complex topics such as Ruby class relationships, Scraper CLIs and ORMs. Personally, I enjoy data manipulation to see if I can spot common trends and make my own deductions based on the resulting data. Nothing encapsulates that better than SQL.

SQL is a domain-specific language and is the standard language for relational database management systems. It's a very powerful tool when it comes to data  management, but for the sake of this blog we will focus on one aspect of SQL, **aggregate functions**. We will be diving deeper into some basic functions:
1. SUM
2. AVG
3. COUNT
4. MAX and MIN

For illustration purposes, let's say we have a celebrities table that holds certain information, such as their name, notable movies, and net worth.

|       name      | age |    notable_movie    |   net_worth  |
| --------------- | --- | ------------------- | ------------ |
| Brad Pitt       |  55 | Fight Club          | $240,000,000 |
| Christoph Waltz |  62 | Inglorious Bastards | $20,000,000  |
| Al Pacino       |  78 | Scarface            | $165,000,000 |

### SUM

The `SUM()` function does exactly what it says, it returns the sum of numbers. Unlike other SQL aggregate functions, the sum function accepts only the expression that evaluates to numerical values. If we want to get the sum of the actor's net worth combined and order it by name, we can write something like:

```
SELECT SUM(net_worth)
FROM celebrities
ORDER BY name;
```

There are two modifiers for the sum function that can be helpful depending on the return we might be looking for:
1. The `DISTINCT` modifier instructs the sum function to calculate the total of distinct values, which means that duplicates are eliminated.
2. The `ALL` modifier allows the sum function to return the sum of all values including duplicates. It is used by default if no modifier is specified explicitly.

### AVG

The `AVG()` function returns an average of a group of numbers. We can use this function to return either the average net worth or the average age of the celebrities in our table. Let's look at the average $$$

```
SELECT AVG(net_worth)
FROM celebrities
ORDER BY name;
```

Just like the sum function, the average function has the `DISTINCT` and `ALL` modifiers available to it.

### COUNT

The `COUNT()` function returns the number of rows present in a table. In this table we have three entries, Brad, Christoph, and Al.

```
SELECT COUNT(*)
FROM celebrities;
```

If we want to find the total count of celebrities with a net worth greater than a hundred million, we can set a conditional after the function:

```
SELECT COUNT(*)
FROM celebrities
WHERE net_worth > 1000000
```

### MAX and MIN

The `MAX()` function returns the maximum value in a set while the `MIN()` function returns the minimum value in a set of values. This time, we want to see the oldest and youngest actors in our table.

```
SELECT MAX(age)
FROM celebrities;
```
This will return Al Pacino which is the senior on the list, 78 years young - _Hooah!_

```
SELECT MIN(age)
FROM celebrities;
```
This will return Brad Pitt, who is 55 years old.
