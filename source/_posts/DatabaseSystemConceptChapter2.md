---
title: DatabaseSystemConcepts・Chapter2 Introduction to the Relational Model
date: 2018-11-14 11:07:21
tags: 
    - database
    - 数据库系统概念
categories: 
    - Learning Notes    
---

In this chapter, we first study the fundamentals of the relational model. 
## Structure of Relational Databases

In the relational model the term<br> **relation** is used to refer to a **table**,<br> while the term **tuple** is used to refer to a **row**. <br>Similarly, the term **attribute** refers to a **column** of a table.<br>

We use the term **relation instance** to refer to a specific instance of a relation,
i.e., containing a specific set of rows.  

**domain**
:    For each attribute of a relation, there is a set of permitted values, 
called the domain of that attribute. <br>A domain is **atomic** if elements of the domain are considered to be indivisible units. 

## Database Schema
differentiate</n>
**database schema** which is the **logical design** of the database
**database instance** which is a **snapshot** of the data in the database at a given instant in time

## Keys

**superkey**
:    A superkey is a set of one or more attributes that, taken collectively, allow us to **identify uniquely** a tuple in the relation. <br>No two tuples in a relation are allowed to have exactly the same value for all attributes.

**primary key**
:    We shall use the term primary key to denote a candidate key that is chosen by the database designer as the principal means of identifying tuples within a relation.   

choose Primary keys:

 - must be chosen with care</n>
   e.g.  the name of a person is obviously not sufficient, because there may be many people with the same name.
 - should be chosen such that its attribute values are never, or very rarely, changed</n>
   e.g. the address field of a person should not be part of the primary key, since it is likely to change. 
 - It is customary to list the primary key attributes of a relation schema **before** the other attributes   

**foreign key**
:    A foreign key is a set of attributes in a referencing relation, such that for each tuple in the referencing relation, the values of the foreign key attributes are guaranteed to occur as the **primary key value** of a tuple in the referenced relation.

## Schema Diagrams
**schema diagrams**
:    depict a database schema, along with primary key and foreign key dependencies
## Relational Operations
**operations**
- The **most frequent operation** is the selection of specific tuples from **a single relation** (say instructor) that **satisfies some particular predicate** (say salary >$85,000). <br> The result is a new relation that is a subset of the original relation (in-structor). 
- Another **frequent** operation is to select certain attributes (columns) from a relation. The result is a new relation having only those selected attributes.
-  **join operation**  
There are a number of different ways to join relations (as we shall see in Chapter 3).
  - natural join
- the Cartesian product operation
- the union operation







   




