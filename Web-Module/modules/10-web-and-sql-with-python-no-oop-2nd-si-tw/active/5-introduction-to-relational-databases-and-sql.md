# Introduction to Relational Databases and SQL

## Introduction

Relational database management systems are a key component of many web sites and applications. They provide a structured way to store, organize, and access information.

On this page, we will go through:

  * **why do people use databases** ,
  * **what are the key terms** in connection with databases,
  * **how do we visualize database models** ,
  * **what is SQL and what are the basic SQL statements**.



## Database vs. Datafile

Until now, we used the file system directly to store information on the long term. First, we used txt files with our own syntax, then we switched to use csv files. There are several problems using files for saving data for our applications:

  * Finding specific pieces of information sometime needs complicated logic. 
  * Files not scale well. If you have 6 "columns" in every row of your csv, you can not just insert a new column between the 2nd and the 3rd columns, you have to rearrange the whole file.
  * Everything is stored as strings.
  * Only one application can open a file at once.
  * .csv files are not compressed -> if you have a lot of lines, you will have a large file.
  * As the file gets larger, reading gets slower.



Some really brilliant thoughts about why we need a database:

[![Play on YouTube](https://img.youtube.com/vi/Ls_LzOZ7x0c/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=Ls_LzOZ7x0c "Play on YouTube")

And in the following videos, you can get some insights for the database fundamentals (the first video covers more basic concepts, the second is more thorough, we suggest to watch each of them):

[![Play on YouTube](https://img.youtube.com/vi/IXycPq7MnwE/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=IXycPq7MnwE "Play on YouTube")

[![Play on YouTube](https://img.youtube.com/vi/xNJZYX6tpWU/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=xNJZYX6tpWU "Play on YouTube")

### Important terms

#### Database engine

A database **engine** (or storage **engine** ) is the underlying software component that a **database management system** ( **DBMS** ) uses to create, read, update and delete (CRUD) data from a database.

Further reading: [Wikipedia](https://en.wikipedia.org/wiki/Database_engine "Wikipedia")

#### SQL

SQL (Structured Query Language) is a special-purpose programming language designed for managing data held in a relational database management system (RDBMS), or for stream processing in a relational data stream management system (RDSMS).

Further reading: [Wikipedia](https://en.wikipedia.org/wiki/SQL "Wikipedia")

#### PostgreSQL

As you can see, there are many relational database management systems you can work with, each has a slightly different implementation of SQL. We will learn **PostgreSQL** , or Postgres, which is a popular choice for many small and large projects and has the advantage of being standards-compliant and having many advanced features like reliable transactions and concurrency without read locks. PostgreSQL is a powerful, open source [object-relational database system](https://en.wikipedia.org/wiki/Object-relational_database). It has more than 15 years of active development and a proven architecture that has earned it a strong reputation for reliability, data integrity, and correctness.

#### Query

A precise request for information retrieval with database and information systems

#### Table / Entity

A table is a collection of related data held in a structured format within a database. It consists of columns, and rows.

#### Record / Row

A row - also called a record or tuple - represents a single, implicitly structured data item in a table.

Each row in a table represents a set of related data, and every row in the table has the same structure.

#### Attribute / Column

A column is a set of data values of a particular simple type, one for each row of the table. The columns provide the structure according to which the rows are composed.

Each column in a table represents the same property of all the records, and every column in the table has the same type.

## Visualization

In every topic we are dealing with visualization adds an extra layer which helps understanding the concept. This is the case with databases as well, where a lot of visualization methods emerged, but the mostly used is the one called [Entity-relationship model](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model) or Entity-relationship Diagram (ERD).

The mostly used notation is the "[Crow's foot notation](http://www.vertabelo.com/blog/technical-articles/crow-s-foot-notation)", so we will use that as well while describing database models. Please read about it on the linked page as it is important to understand this concept (you can read about other notations at the end of the linked page).

You can also find a [cheat sheet here](https://drive.google.com/file/d/0B_spkK3eZiHmZTZhczVTaVZxUFU/view) which covers the basic cardinality types between entities.

## SQL Statements

To read about SQL statements, please read the following pages (order matters):

  1. <http://www.w3schools.com/sql/sql_syntax.asp>
  2. <http://www.w3schools.com/sql/sql_select.asp>
  3. <http://www.w3schools.com/sql/sql_orderby.asp>
  4. <http://www.tutorialspoint.com/postgresql/postgresql_limit_clause.htm>
  5. <http://www.w3schools.com/sql/sql_where.asp>[LINK](http://www.w3schools.com/sql/sql_where.asp)
  6. <http://www.w3schools.com/sql/sql_like.asp>
  7. <http://www.w3schools.com/sql/sql_null_values.asp>
  8. <http://www.w3schools.com/sql/sql_and_or.asp>
  9. <http://www.w3schools.com/sql/sql_insert.asp>
  10. <http://www.w3schools.com/sql/sql_update.asp>
  11. <http://www.w3schools.com/sql/sql_delete.asp>


