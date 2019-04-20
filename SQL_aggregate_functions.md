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

**SUM()** does exactly what it says, it returns the sum of numbers. Unlike other SQL aggregate functions, the sum function accepts only the expression that evaluates to numerical values. If we want to get the sum of the actor's net worth combined and order it by name, we can write something like:

```
SELECT SUM(net_worth)
FROM celebrites
ORDER BY name;
```
