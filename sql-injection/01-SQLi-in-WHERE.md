# Lab: SQL Injection in WHERE Clause

**Difficulty:** Apprentice
**Category:** SQL Injection
**Lab URL:** https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data

## Vulnerability
SQL Injection

## Root Cause
User input (`category`) is not sanitized before being used in SQL query.

## Original Query
```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

## Payload
```sql
Gifts' OR 1=1--
```

## Why it Works
-- Makes the rest of the query a comment
1=1 is always true

## Impact
Attacker can read data that they shouldn't be able to see
