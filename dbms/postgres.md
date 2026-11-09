# PostgreSQL

PostgreSQL is a powerful, open-source, client-server relational database system with strong support for SQL standards, 
data integrity, and advanced features.

Think of PostgreSQL not as a replacement for fopen() (like SQLite), but as a full database server like Oracle or MySQL.

## Basic Commands

### Connect to PostgreSQL

```bash
psql -U username -d database_name

Or from inside psql:

\c database_name

Ex : psql -U postgres -d satyam
```

### Show connection info

```bash
# show connection info
\conninfo

# switch to new db
\c new_database
```

### Create DB

```sql
# Create database
CREATE DATABASE database_name;

# Show current DB
SELECT current_database();
```

### Show tables in DB

```bash
\dt
```

### Show schema of table

```bash
\d person
```

### Output data in CSV file

```bash
\copy person TO 'output.csv' CSV HEADER;
```
### Execute a script

```bash
psql -U username -d dbname -f script.sql
Or inside psql:
# for current directory 
\i script.sql

\i '/Users/satyam/Downloads/script.sql'
```
### Show current working directory

```bash
# show current working directory
\! pwd

# change directory to given directory
\cd referential-integrity 
```

## Data Types

PostgreSQL has strict and rich data types.

Examples:
	•	INTEGER, BIGINT
	•	NUMERIC, REAL
	•	TEXT, VARCHAR(n)
	•	BOOLEAN
	•	DATE, TIMESTAMP
	•	JSON / JSONB
	•	UUID
	•	ARRAY types

Unlike SQLite, PostgreSQL enforces column types strictly.

```sql
CREATE TABLE test(age INTEGER);
INSERT INTO test VALUES('hello');  -- ERROR
```

PostgreSQL column type = strict rule, not suggestion.

## Design Philosophy

Client-Server Architecture

PostgreSQL runs as a database server process.
Applications connect via TCP or Unix socket.

Perfect for:
	•	Web apps
	•	Microservices
	•	Enterprise systems


Strong Data Integrity

PostgreSQL supports:
	•	Foreign Keys
	•	CHECK constraints
	•	UNIQUE constraints
	•	Transactions (ACID)
	•	MVCC (Multi Version Concurrency Control)

Example:

```sql
CREATE TABLE student(
    id SERIAL PRIMARY KEY,
    name TEXT
);

CREATE TABLE enrollment(
    student_id INT REFERENCES student(id)
);
```

## Advanced Features

PostgreSQL supports:
	•	Stored procedures
	•	Window functions
	•	Full-text search
	•	JSON queries
	•	Index types (GIN, GiST, BRIN)
	•	Partitioning
	•	Extensions (PostGIS, TimescaleDB)

Reliability + Scalability
	•	Crash safe
	•	Replication
	•	Backups
	•	High concurrency

Not Zero-Config

Requires:
	•	Installation
	•	User accounts
	•	Port (default 5432)
	•	Config files

But gives much more control.

## Storage Philosophy

In PostgreSQL:

👉 Type belongs to column
👉 Value must match type

Opposite of SQLite’s flexible typing.


## When to Use PostgreSQL vs SQLite

Use SQLite	        Use PostgreSQL
Local tools	        Web apps
Mobile apps	        Production backend
Single user	        Multi user
Embedded storage	API servers
Prototyping	        Real scalable system

For Spring Boot projects, start with SQLite for learning, then move to PostgreSQL for production-ready systems.

Mental Model
	•	SQLite → HashMap saved to disk
	•	PostgreSQL → Full database server system