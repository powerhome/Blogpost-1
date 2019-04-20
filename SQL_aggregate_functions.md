# The Power of SQL Aggregate Functions

Throughout my first few months, there has been so many topics we had to cover from basic Ruby conditionals and iterations, to more complex topics such as Ruby class relationships, Scraper CLIs and ORMs. Personally, I enjoy data manipulation to see if I can spot common trends and make my own deductions based on the resulting data. Nothing encapsulates that better than SQL.

SQL is a domain-specific language and is the standard language for relational database management systems. It's a very powerful tool when it comes to data  management, but for the sake of this blog we will focus on one aspect of SQL, **aggregate functions**. We will be diving deeper into some basic functions:
1. SUM
2. AVG
3. COUNT
4. MAX
5. MIN

For illustration purposes, let's say we have a celebrities table that holds certain information, such as their name, notable movies, and net worth.

|       name      | age |    notable_movie    |   net_worth  |
| --------------- | --- | ------------------- | ------------ |
| Brad Pitt       |  55 | Fight Club          | $240,000,000 |
| Christoph Waltz |  62 | Inglorious Bastards | $20,000,000  |
| Al Pacino       |  78 | Scarface            | $165,000,000 |

### SUM

`SUM()` does exactly what it says, it returns the sum of numbers. Unlike other SQL aggregate functions, the sum function accepts only the expression that evaluates to numerical values. If we want to get the sum of the actor's net worth combined and order it by name, we can write something like:

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
