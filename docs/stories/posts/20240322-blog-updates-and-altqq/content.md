---
authors:
  - baluyotraf
date: 
    created: 2024-03-22
    updated: 2024-03-24
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

This library should help you if you have the following issues:

*   Errors from passing incorrect parameter values because due to lack of 
    naming and typing
*   Issue with merging parameter values from complex and nested queries
*   Lack of ability to easily nest and reuse existing queries

You can read more details on [Why use Alternative Queries?] section of the
documentation.

[MkDocs Material Documentation]: https://squidfunk.github.io/mkdocs-material/
[Software+ML Code]: https://github.com/baluyotraf/softwareplusml
[Why use Alternative Queries?]: https://altqq.baluyotraf.com/stable/rationale/