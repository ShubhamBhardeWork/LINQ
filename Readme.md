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
   - Projection or transfromation of data.

1. .SelectMany()
   - Flatten nested collections.

1. .Where()
   - Filters data.

1. .FirstOrDefault()
   - Returns `first matching element` or `default value` if not found.

1. .SingleOrDefault()
   - Returns `single matching element` or `default value` if not found.

1. .Contains()
   - Checks whether a value exists or not in a collection 
   
1. .Any()
   - Checks whether at least one element satisfy a condition.
   - Any() method is optimized for existence checking because it stops once match is found.

1. .All()
   - Checks whether all elements satisfy a condition.

1. .Count()
   - Returns the total number of elements.

1. .Distinct()
   - return Unique values/elements (Removes duplicates)
   
1. .OrderBy()
   - Sorts data in ascending order.

1. .OrderByDescending()
   - Sorts data in descneding order.

1. .ThenBy()
   - Secondary sorting data in ascending order.

1. .ThenByDescending()
   - Secondary sorting data in descneding order.

1. .Skip()
   - Skips a specified number of elements.

1. .Take()
   - Returns a specified number of elements.

1. .GroupBy()
   - Groups elements based on a key.

1. .Join()
   - Combines two collections based on a common key.

1. .ToArray()
   - Convert to Array.

1. .ToList()
   - Convert to List.

1. .First()
   - Returns the `first matching element` else `exception`.

1. .Single()
   - Returns `exactly one matching record` else `exception if no record or multiple records found`.




## Best Practices
- Use IQueryable before fetching data.

- Use projection (Select) instead of fetching whole entity.

- Use AsNoTracking() for read-only operations.

- Avoid early ToList().

- Use pagination for huge data.

- Use async methods in EF Core: