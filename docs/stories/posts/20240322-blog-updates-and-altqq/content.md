---
authors:
  - baluyotraf
date: 
    created: 2024-03-22
categories:
  - software
  - data
---

# Blog Updates and Alternative Queries

Today, I would like to announce some blog updates and the release of my SQL
helper library, Alternative Queries (altqq).

<!-- more -->

## Blog Updates

As of today, the blogs in the page are powered by MkDocs Material's blog
plugin. This means that the blog page will now have additional features such
as archive, categories, and previews. If you're interested in creating blogs,
be sure to check the [MkDocs Material Documentation]. If you're not aware how
to start, you can check the [Software+ML Code].

## Alternative Queries

If you work a lot with handcrafted SQL queries and prefer to have type-checked
parameters, and reusable queries, feel free to check my library called
Alternative Queries (altqq). 

### Managing Ordered Parameters

Alternative Queries also allows you to manage your query parameters. For 
example, for ODBC databases, `pyodbc` does not allow named parameter. If means 
that to reuse queries, one needs to make note of the parameters, as they must
be in order. For example

```python
query1 = """SELECT * from "Users" where "Id" = ?"""
query2 = """SELECT * from "Users" where "Name" = ?"""

full_query = f"{query1} UNION ALL {query2}"
parameters = [uuid4(), "Arie"]
```

The simple above looks simple, but if `query1` takes 3 parameters, and the 
`full_query` reuses 3-5 existing queries, the scenario becomes more complex.
Even in this case, there is a possibility to define `parameters` as 
`["Arie", uuid4()]` if one is not careful.

### Managing Named Parameters

`psycopg` support is not yet implemented in the current version. But as an
example, `psycopg` provides named parameters. The advantage of named parameters
are obvious: no parameter repetition, and more context from parameter names.

```python
query1 = """SELECT * from "Users" where "Id" = %(id)s"""
query2 = """SELECT * from "Users" where "Name" = %(name)s"""

full_query = f"{query1} UNION ALL {query2}"
parameters = {"id": uuid4(), "name": "Arie"}
```

This solution already looks better. There's no way of mistaking the query
parameters, even if the queries are merged improperly. However, this can be
an issue if the queries are complex and a lot of reuse is required. It is
possible to merge different queries that require the same name.

If you find these problems interesting, check the [Alternative Queries Documentation] 
and play around it by downloading the [Alternative Queries Package].

[MkDocs Material Documentation]: https://squidfunk.github.io/mkdocs-material/
[Software+ML Code]: https://github.com/baluyotraf/softwareplusml
[Alternative Queries Documentation]: https://altqq.baluyotraf.com/stable/
[Alternative Queries Package]: https://pypi.org/project/altqq/