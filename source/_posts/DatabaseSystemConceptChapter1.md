---
title: DatabaseSystemConcepts・Chapter1 Introduction
date: 2018-11-13 23:00:11
tags: 
    - database
    - 数据库系统概念
categories: 
    - Learning Notes
---


## Database-System Applications

 - Enterprise Information
 - Banking and Finance
 - Universities
 - Airlines
 - Telecommunication
## Purpose of Database Systems
文件处理系统file-processing system **major disadvantages**

 - data redundancy and inconsistency
 - difficulty in accessing data
 - data isolation
 - integrity problem
 - atomicity problem
 - concurrent-access anomaly
 - security problem
 
## View of Data
 A major purpose of a database system is to provide users with an ***abstract view*** of the data.
### 数据抽象Data Abstraction
 - physical level
 :     The lowest level<br>
describes **how** the data are actually stored

 - logical level
 :    The next-higher level<br>
   describes **what** data are stored in the database, and what **relationships** exist among those data

 - view level
 :    The highest level 

```graph
    A[view 1] -->B(logical level)
    C[view 2] -->B(logical level)
    D[view n] -->B(logical level)
    B(logical level) -->E[physical level]
```
### 实例和模式Instances and Schemas
instance
:    The collection of information stored in the database at a particular moment

schema
:    The overall design of the database 

### 数据模型Data Models
data model
:    a collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints.

## Database Languages
### Data-Manipulation Language(DML)
types of access
:    

 - Retrieval
 - Insertion
 - Deletion
 - Modification

query
:    A query is a statement requesting the retrieval of information. 

### Data-Definition Language(DDL)
**consistency constraints**
can be tested with minimal overhead:

 - Domain Constraints
domain eg: integer types, character types, date/time types
 - Referential Integrity
 - Assertions
 eg: “Every department must have at least five courses offered every semester” must be expressed as an assertion. 
 - Authorization
 - read authorization, insert authorization, update authorization, delete authorization
 
## Relational Databases
### Data-Manipulation Language
The SQL query language is nonprocedural. 
### Data-Definition Language
SQL provides a rich DDL that allows one to define tables, integrity constraints,
assertions, etc.
### Database Access from Application Programs
To access the database, DML statements need to be executed from the host
language. There are two ways to do this: 

 - By providing an application program interface<br>
 eg:The Java Database Connectivity (JDBC) standard provides corresponding features
to the Java language.
 - DML precompiler<br>
 converts the DML statements to normal procedure calls in the host language

## Database Design
### Design Process

 1. characterize fully the data **needs** of the prospective database users. 
  The outcome of this phase is a specification of user **requirements**.
 2. the designer chooses a data model, **translates** these requirements into a conceptual schema
 of the database. 
 The focus at this point is on describing the data and their relationships, rather than on specifying physical storage details.
 3. logical-design phase
 4. physical-design phase
 
### The Entity-Relationship Model
 entity-relationship (E-R) diagram
:    The overall logical structure (schema) of a database can be expressed graphically by an entity-relationship (E-R) diagram.<br> 
most popular way to draw these diagrams: Unified Modeling Language (UML)

### Normalization
Among the undesirable properties that a **bad design** may have are:

- Repetition of information
- Inability to represent certain information

## Data Storage and Querying
The functional components of a database system can be broadly divided into: 

- storage manager   
- query processor components

### Storage Manager
The storage manager is responsible for the interaction with the file manager. 
storing, retrieving, and updating data in the database

The storage manager **components** include:

 - Authorization and integrity manager
 - Transaction manager
 - File manager
 - Buffer manager

several data structures:

 - Data files
 - Data dictionary
 - Indices

### The Query Processor
The query processor components include:

 - DDL interpreter
 - DML compiler
 - Query evaluation engine
 

## Transaction Management
transaction
:    A transaction is a collection of operations that performs a single logical
function in a database application. Each transaction is a unit of both **atomicity**
and **consistency**.

The transaction manager consists of :

- the **concurrency-control manager**
- the **recovery manager**

## Database Architecture

![figure1_5](20181114figure1_5.png) 

## Data Mining and Information Retrieval
 data mining
 :    The term data mining refers loosely to the process of semiautomatically analyzing
large databases to find useful patterns. <br>
information retrieval
:    the emphasis in the field of information systems is different from that in database systems, concentrating on issues such as 

 - querying based on keywords; 
 - the relevance of documents to the query; 
 - the analysis, classification, and indexing of documents. 

## Specialty Databases
### Object-Based Data Models
The major database vendors presently support the object-relational data model, 
a data model that combines features of the **object-oriented data model** and **relational data model**. 
### Semistructured Data Models
Semistructured data models permit the specification of data where individual
data items of the same type may have **different sets of attributes**.

## Database Users and Administrators
### Database Users and User Interfaces
 Different types of user interfaces have been designed for the different types of users.
### Database Administrator
The functions of a DBA include:

 - Schema definition.
 - Storage structure and access-method definition.
 - Schema and physical-organization modification. 
 - Granting of authorization for data access. 
 - Routine maintenance.
   - Periodically **backing up the database**, either onto tapes or onto remote
servers, to prevent loss of data in case of disasters such as flooding.
   - Ensuring that **enough free disk space** is available for normal operations,
and upgrading disk space as required.
   - **Monitoring** jobs running on the database and ensuring that performance
is not degraded by very expensive tasks submitted by some users.

