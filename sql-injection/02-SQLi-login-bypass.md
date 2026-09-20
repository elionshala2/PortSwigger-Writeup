# Lab: SQL injection vulnerability allowing login bypass

**Difficulty:** Apprentice

**Category:** SQL Injection

**Lab URL:** https://portswigger.net/web-security/sql-injection/lab-login-bypass

## Vulnerability
SQL Injection

## Root Cause
User input (`username`) is not sanitized before being used in SQL query.

## Original Query
```sql
SELECT * FROM users WHERE username = '' AND password = ''
```

## Payload
```sql
administrator'--
```

## Why it Works
-- Makes the rest of the query a comment
'administrator' is the username, the rest of the query is a comment, so it logs you in without requesting a password

## Impact
Attacker can steal accounts (`in this case administrator account`)