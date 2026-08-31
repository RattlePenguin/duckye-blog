+++
title = "Repository Patterns in Databases"
description = "Not GitHub Repository."
date = "2026-08-13"
author = "Benedict Setiawan"
draft = "true"
+++

## Introduction

In my recent project [AusFencer](/aus-fencer), I was introduced to the
**Repository Pattern**, a technique with goals of ...

## The Problem

In AusFencer, there are two main data types, a Fencer and a Bout.
Both Fencers and Bouts require basic CRUD, operating over two layers.
I store data in an SQLite database, retrieve data using SQL queries, and
format them into JSON and HTTP responses.

I would have multiple threads, each making requests to my SQLite database,
all needing different types of queries and entries.
This would inevitably be ugly.
Foreseeing a very messy future, I decided to approach this differently.

This ends up covering many strong principles in programming, particularly
encapsulation and modularisation.
By separating
This also gives rise to the Single Responsibility Principle,
where each function or method should just do one thing, and do it well.
Without the repository, a function that pulls Fencers from the database
would not only need the correct SQL query,
it would also have to format it into JSON, resolve errors, and
package the HTTP response.

## Conclusion

If you are working with a database and distinct data types, try
using the repository pattern!
Sure it's a bit of a hassle, but when one entity is in charge of
handling every request for data, things can get out of hand
quickly.
The best part is, this isn't limited to databases.
I extended this to HTTP handlers, which is a similar concept where
instead of data, the handler encapsulates
