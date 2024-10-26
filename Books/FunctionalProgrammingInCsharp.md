# Functional Programming in C# - Enrico Buonanno

## Chapter 1

- What exactly is functional programming? At a very high level, it’s a programming style that
emphasizes functions while avoiding state mutation. 
- The reason you see both the functional and nonfunctional approaches in the framework is
historical: `List<T>.Sort` predates LINQ, which marked a decisive turn in a functional direction.
- There are several language constructs in C# that you can use to represent functions:
    - Methods
    - Delegates
    - Lambda expressions
    - Dictionaries
- If your function is short and you don’t need to reuse it elsewhere, lambdas offer the most
attractive notation.
- Use function pointers in LINQ clauses for better readablility. 
- HOFs also have some drawbacks:
    - You’ve increased stack use. There’s a performance impact, but it’s negligible.
    - Debugging the application will be a bit more complex because of the callbacks.
- Use **HOFs** when appropriate, but be mindful of readability: use short lambdas, clear naming, and meaningful indentation.

## Chapter 2 - Function Purity

- PLINQ is an implementation of LINQ to Objects that works in parallel.
- Static methods can cause problems if they do either of the following:
    - Act on mutable static fields
    - Perform I/O
- When a function is pure, there’s no downside to making it static. As a general guideline,
    - Make pure functions static.
    - Avoid mutable static fields.
    - Avoid direct calls to static methods that perform I/O.


## Others

- Use higher-order functions with LINQ and avoid writing your own for-loops.Try to avoid unnecessary repetition. For many things, there are generic algorithms. Use LINQ and other Algorithms to create powerful abstractions. If there is not an algorithm available, try to be generic and write your own algorithms.

| Task | Linq |
|------|------|
| Projection |	Select, SelectMany |
| Aggregation |	Aggregate, Sum, Min, Max, Average, Count |
| Restriction |	Where |
| Existence |	Any, All, Contains, Distinct |
| Set Operations |	Contains, Distinct, Union, Intersect, Except |
| Sorting |	OrderBy, ThenBy, OrderByDescending, ThenByDescending |
| Paging |	First, Last, Single, Skip, Take, SkipWhile, TakeWhile |
| String | Formating	string.Format() or use $"" (String interpolation) |