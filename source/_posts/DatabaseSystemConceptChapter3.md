---
title: DatabaseSystemConcepts・Chapter3 Introduction to SQL
date: 2018-11-14 16:42:25
tags: 
    - database
    - 数据库系统概念
categories: 
    - Learning Notes    
---

## Overview of the SQL Query Language
The SQL language has several parts:
- **Data-definition language (DDL)**
- **Data-manipulation language (DML)**
- **Integrity**
- **View definition** 
:    The SQL DDL includes commands for defining views.
- **Transaction control**
:    SQL includes commands for specifying the **beginning** and **ending** of transactions.
- **Embedded SQL** and **dynamic SQL**
:    define how SQL statements can be embedded within general-purpose programming languages, such as C, C++, and Java.
- **Authorization**
:     The SQL DDL includes commands for specifying access rights to relations and views.

## SQL Data Definition 

The SQL DDL allows: 
- specification of a set of relations
- information about each relation

including:
• The schema for each relation.
• The types of values associated with each attribute.
• The integrity constraints.
• The set of indices to be maintained for each relation.
• The security and authorization information for each relation.
• The physical storage structure of each relation on disk.

### Basic Types
- char()
- varchar()
- int
- smallint
- numeric(p,d)
- real, double precision
- float()

### Basic Schema Definition
SQL supports a number of different **integrity constraints**. </n>
a few of them: 
•  **primary key**
The primarykey attributes are required to be **nonnull** and **unique**.
•  **foreign key**
must correspond to values of the primary key attributes of some tuple in another
relation 
•  **not null**

SQL prevents any update to the database that violates an integrity constraint.

## Basic Structure of SQL Queries
select, from, where
### Queries on a Single Relation

elimination of duplicates: 
```sql
select distinct dept name
from instructor;
```
arithmetic expression of **select**:
```sql
select ID, name, dept name, salary * 1.1
from instructor;
```

### Queries on Multiple Relations

```sql
select A1, A2, . . . , An
from r1, r2, . . . , rm
where P;
```
**operational order**: first **from**, then **where**, and then **select**.<br>
In general, the meaning of an SQL query can be understood as follows:
1. Generate **a Cartesian product** of the relations listed in the **from** clause
2. Apply the predicates specified in the **where** clause on the result of Step 1.
3. For each tuple in the result of Step 2, output the attributes (or results of expressions) specified in the **select** clause.

### The Natural Join
**natural join**
:    The natural join operation operates on two relations and produces a relation as the result. 
```sql
select name, course id
from instructor, teaches
where instructor.ID= teaches.ID;
```
=
```sql
select name, course id
from instructor natural join teaches;
```
*※both the tuple from instructor and the tuple from teaches have the same value on the common attribute, ID.*
```sql
select name, title
from instructor natural join teaches, course
where teaches.course id= course.course id;
```
≠
```sql
select name, title
from instructor natural join teaches natural join course;
```
*teaches contains the attributes
(ID, name, dept_name, salary, course_id, sec_id)*
*course relation contains the attributes 
(course_id, title, dept_name, credits)*
```sql
select name, title
from instructor natural join teaches, course
where teaches.course id= course.course id;
```
=
```sql
select name, title
from (instructor natural join teaches) join course using (course id);
```

## Additional Basic Operations
### The Rename Operation
reasons to remame:
- replace a long relation name with **a shortened version** that is more convenient to use elsewhere in the query
e.g.
```sql
select T.name, S.course id
from instructor as T, teaches as S
where T.ID= S.ID;
```
-  a case where we wish to compare tuples in the **same relation**
e.g.
```sql
select distinct T.name
from instructor as T, instructor as S
where T.salary > S.salary and S.dept name = ’Biology’;
```
*“Find the names of all instructors who earn more than the lowest paid instructor in the Biology department.” *

### String Operations
- operator **like**
 - Percent (%)
 e.g.
   - 'Intro%' matches any string beginning with “Intro”
 - Underscore ( _ )
e.g. 
    - '_ _ _' matches any string of exactly three characters.
    - '_ _ _%' matches any string of at least three characters.

- escape character \
  - like ’ab\%cd%’ escape ’\’ matches all strings beginning with “ab%cd”.
  - like ’ab\\cd%’ escape ’\’ matches all strings beginning with “ab\cd”.

### Where Clause Predicates
**between**
```sql
select name
from instructor
where salary between 90000 and 100000;
```
=
```sql
select name
from instructor
where salary <= 100000 and salary >= 90000;
```
<br>
**(a1, a2) = (b1, b2), (a1, a2) <= (b1, b2)...**
```sql
select name, course id
from instructor, teaches
where instructor.ID= teaches.ID and dept name = ’Biology’;
```
=
```sql
select name, course id
from instructor, teaches
where (instructor.ID, dept name) = (teaches.ID, ’Biology’);
```

## Set Operations
### The Union Operation
The union operation automatically **eliminates duplicates**, unlike the select clause.

*To find the set of all courses taught either in Fall 2009 or in Spring 2010, or both:*
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
union
(select course id
from section
where semester = ’Spring’ and year= 2010);
```
retain all duplicates, we must write **union all** in place of union:
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
union all
(select course id
from section
where semester = ’Spring’ and year= 2010);
```

### The Intersect Operation
The intersect operation automatically **eliminates duplicates**. 
*To find the set of all courses taught in the Fall 2009 as well as in Spring 2010 we write:*
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
intersect
(select course id
from section
where semester = ’Spring’ and year= 2010);
```
retain all duplicates, we must write **intersect all** in place of intersect:
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
intersect all
(select course id
from section
where semester = ’Spring’ and year= 2010);
```

### The Except Operation
The except operation
- performs set difference: outputs all tuples from its first input that do not occur in the second input
-  automatically eliminates duplicates 
*To find all courses taught in the Fall 2009 semester but not in the Spring 2010 semester, we write:*
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
except
(select course id
from section
where semester = ’Spring’ and year= 2010);
```
retain all duplicates, we must write **except all** in place of except:
```sql
(select course id
from section
where semester = ’Fall’ and year= 2009)
except all
(select course id
from section
where semester = ’Spring’ and year= 2010);
```

## Null Values
the definitions of the **Boolean operations** are extended to deal with the value **unknown**.<br>
**and**:
- The result of true and unknown is unknown
- false and unknown is false
-  unknown and unknown is unknown

**or**:
- The result of true or unknown is true, 
- false or unknown is unknown
- unknown or unknown is unknown

**not**:
-  The result of not unknown is unknown

if **unknown** in the result of "where"?
**No**. If the where clause predicate evaluates to either false or unknown for a tuple,
that tuple is not added to the result.
<br>
Use keyword **null** (`where XX is null`, `where XX is not null`).
<br>
How the **select distinct** treats **null** ?
{(’A’,null), (’A’,null)}, are treated as being **identical**, even if some of the attributes have a null value. 
The values are treated as identical if either both are non-null and equal in value, or both are null. 
<br>
What the result of “null=null”?
It would return **unknown**, rather than true.

## Aggregate Functions
• Average: avg
• Minimum: min
• Maximum: max
• Total: sum
• Count: count

### Basic Aggregation
```sql
select avg (salary) as avg salary
from instructor
where dept name= ’Comp. Sci.’;
```
```sql
select count (*)
from course;
```
### Aggregation with Grouping
**group by**

<i class="fa fa-exclamation fa-2x"></i> it is **important** to ensure that the only attributes that appear in the select statement without being aggregated are those that are present in the group by clause.
**e.g.**　 the following query is **erroneous** since ID does not appear in the group by clause, and yet it appears in the select clause without being aggregated:
```sql
/* erroneous query */
select dept name, ID, avg (salary)
from instructor
group by dept name;
```
### The Having Clause
(What's the  **sequence** of operations ?)
The meaning of a query containing **aggregation, group by, or having clauses** is defined by the following **sequence** of operations:
1. the **from** clause is first evaluated to get a relation.
2. If a **where** clause is present, the predicate in the where clause is applied on the result relation of the from clause.
3. Tuples satisfying the where predicate are then placed into groups by the **group by** clause if it is present.<br> If the group by clause is absent, the entire set of tuples satisfying the where predicate is treated as being in one group.
4. The **having** clause, if it is present, is applied to each group;<br>the groups that do not satisfy the having clause predicate are removed.
5. The **select** clause uses the remaining groups to generate tuples of the result of the query, <br>applying the aggregate functions to get a single result tuple for each group.

<br>
<br>
<br>
- [ ] todo **这里要写个流程图**

### Aggregation with Null and Boolean Values
<i class="fa fa-exclamation fa-2x"></i> aggregate functions treat nulls according to the following rule:
1. All aggregate functions **except count (*)** ignore null values in their input collection.
2. As a result of null values being ignored, the collection of values may be empty.
  1. The **count** of an empty collection is defined to be **0**
  2. all other aggregate operations return a value of **null** when applied on an empty collection. 

## Nested Subqueries
A subquery is a select-from-where expression that is nested within another query <br>(subqueries **in the where clause**). 
### Set Membership
The **in** connective:
tests for set membership, where the set is a collection of values produced by a select clause. 
The **not in** connective:
tests for the absence of set membership.

### Set Comparison
**SOME**
 The phrase “greater than at least one” is represented in SQL by > **some**. 
 e.g.
 ```sql
 select name
from instructor
where salary > some (select salary
from instructor
where dept name = ’Biology’);
```
**some and in**:
- **= some** is identical to **in**
- **<> some** is **not** the same as **not in**
<br>

**ALL**
 The construct > **all** corresponds to the phrase “greater than all.” 
 e.g.
```sql
select name
from instructor
where salary > all (select salary
from instructor
where dept name = ’Biology’);
```
**all and in**:
- **<> all** is identical to **not in**
- **all** is not the same as **in**

### Test for Empty Relations

