# Simplified SQL Query Engine
An SQL engine which can execute a query written in a simplified form of Structured Query Language (SQL) against a simple database.

## Requirements 
This repo requires Rust setup and installed, if not installed click on the given link for Rust setup and installation. 
For macOS, Linux, or another Unix-like OS - https://www.rust-lang.org/tools/install
For windows - https://forge.rust-lang.org/infra/other-installation-methods.html

## Simplified SQL
This SQL query engine handles a simplified version of SQL, supporting the following features:

* A **SELECT** clause, with any number of columns.
* A **FROM** clause, which identifies the primary table to select records from.
* Any number of optional **JOIN** clauses, treated as **INNER JOINs**.
*An optional WHERE clause with only one condition.

Unsupported Features
The engine does not support:

* Aliases (AS or [bracketed names]).
* CASTing.
* ORDER BY, GROUP BY, COUNT, or EXISTS.
* IN or LIKE, or any other operator other than simple equality, inequality, and greater than/less than.
* AND or OR; only a single WHERE condition is allowed.

## SQL grammar
The SQL queries must adhere to the following EBNF grammar:

```text
query         =  select, ws, from, [ ws, join ], [ ws, where ] ;
select        =  "SELECT ", column-id, [ { ", ", column-id } ] ;
from          =  "FROM ", table-name, [ { ws, join } ] ;
join          =  "JOIN ", table-name, " on ", value-test ;
where         =  "WHERE ", value-test ;
value-test    =  value, comparison, value;
column-id     =  table-name, ".", column-name ;
table-name    = ? a valid SQL table name ? ;
column-name   = ? a valid SQL column name ? ;
value         =  column-id | const
comparison    =  " = " | " > " | " < " | " <= " | " >= " | " <> " ;
const         =  ? a number ? | ? a SQL single-quoted string ? ;
ws            = " " | "\n" | ws, ws ;
```

Note that SQL is not case sensitive; `SELECT` and `select` are equivalent.

### Valid Table and Column Names
A "valid SQL table/column name" is a name containing only letters, numbers, and the '_' character, with no spaces (`/[a-zA-Z0-9_]+/`).

## Getting Started

### Prerequisites
Ensure you have the following software installed before proceeding:

**Rustc**: Necessary to compile rust code.

### Installation

**1. Clone the Repository**:
Clone the project to your local machine using the following command:
```bash
git clone https://github.com/hiten52/Simple-SQL-Engine.git
```

**2. Navigate to the Project Directory**:
Change into the project directory:
```bash
cd Simple-SQL-Engine
```

**3. Type your query in "query" file**

**3. Run the Project**:
Run the project using Cargo:
```bash
cargo run
```
