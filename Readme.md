# LINQ
## What is LINQ:-
- LINQ Stands for Language Integrated Query.

- It is a C# feature that allows developers to query and manipulate data from different data sources like collections and databases using a consistent and type-safe syntax.

- It works with:-
    1. Collections [List, Array]
    1. Databases [Entity Framework Core]
    1. XML & JSON

## Why LINQ?
- Improves readability.
- Reduces boilerplate code [Avoids long loops and manual filtering]
- Strongly typed (compile-time checking).
- Easy filtering, sorting, grouping, projection.
- Common syntax for multiple data sources.


## Types of LINQ:-
1. LINQ to Objects
1. LINQ to Entities
1. LINQ to SQL


## LINQ Syntax Types:-
1. Query Syntax
1. Method Syntax (most preferred & widely used in industry)


## Deferred Execution:-
- Deferred Execution means query does not execute immediately when defined.

- LINQ query executes only when data is actually iterated or materialized.

- Improves performance by avoiding unnecessary execution.

**NOTE:- Deferred execution is useful because query composition can happen before actual execution.**


## Immediate Execution:-
- Query executes immediately and stores result in memory.

### Immediate Execution Methods:-
1. .ToList()
1. .ToArray()
1. .Count()
1. .First() & .FirstOrDefault()
1. .Single() & .SingleOrDefault()



## IEnumerable vs IQueryable:-
### IEnumerable:-
- Works with in-memory collections
- Data fetched first, then filtering happens in memory
- used in LINQ to Objects
- Less efficient for huge data

```cs
IEnumerable<User> users = context.Users.ToList();

var filteredUsers = context.Users.ToList().Where(x => x.Age > 20);
```

### IQueryable:-
- Works with databases
- Filtering happens at database level
- used in LINQ to Entities
- Better performance for huge data
- IQueryable fetches only required data from database, reducing memory usage and improving performance.
- IQueryable supports deferred execution and query composition before execution.

```cs
IQueryable<User> users = context.Users;

var filteredUsers = context.Users.Where(x => x.Age > 18);
```

```I avoid calling ToList() too early because it fetches all data into memory. I prefer filtering with IQueryable before materializing data to improve performance and reduce memory usage.```

**NOTE:- IQueryable converts LINQ queries into SQL and executes them on the database side.**


## LINQ Execution Flow in EF Core:-
```sh
LINQ Query
   ↓
Expression Tree
   ↓
EF Core Converts to SQL
   ↓
SQL Executes in Database
   ↓
Data Returned
```


## LINQ Methods:-
1. .Select()
1. .SelectMany()
1. .Where()
1. .FirstOrDefault()
1. .SingleOrDefault()
1. .Contains()
1. .Any()
1. .All()
1. .Count()
1. .Distinct()
1. .OrderBy()
1. .OrderByDescending()
1. .ThenBy()
1. .ThenByDescending()
1. .Skip()
1. .Take()
1. .GroupBy()
1. .Join()
1. .ToArray()
1. .ToList()
1. .First()
1. .SIngle()


## Best Practices
- Use IQueryable before fetching data.

- Use projection (Select) instead of fetching whole entity.

- Use AsNoTracking() for read-only operations.

- Avoid early ToList().

- Use pagination for huge data.

- Use async methods in EF Core: