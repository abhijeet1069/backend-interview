# Datetime functions

## Current date and time

```sql
-- current date
-- 2026-11-04
select CURRENT_DATE;

-- current time with timezone 
-- 20:12:09.849825+05:30
select CURRENT_TIME;

-- current date and time
-- 2026-11-04 20:13:21.86955+05:30
select CURRENT_TIMESTAMP;

-- current transaction timestamp
-- 2026-11-04 20:16:18.429859+05:30
select NOW();

-- current time without timezone
-- 20:14:16.230142
select LOCALTIME;

-- current timestamp without timezone
-- 2026-11-04 20:15:14.598704
select LOCALTIMESTAMP;
```

## Extract parts of a date

EXTRACT() retrieves individual date components

```sql
-- 2026
SELECT EXTRACT(YEAR FROM DATE '2026-11-04');

-- 11
SELECT EXTRACT(MONTH FROM DATE '2026-11-04');

-- 4
SELECT EXTRACT(DAY FROM DATE '2026-11-04');

-- 15
SELECT EXTRACT(HOUR FROM TIMESTAMP '2026-11-04 15:30:45');

-- 30
SELECT EXTRACT(MINUTE FROM TIME '15:30:45');

```

## Date arithmetic

```sql
-- Add 5 days
-- 2026-11-09
SELECT CURRENT_DATE + 5;

-- Subtract 10 days
-- 2026-10-25
SELECT CURRENT_DATE - 10;

-- Add 2 months
-- 2027-01-04 00:00:00
SELECT CURRENT_DATE + INTERVAL '2 months';

-- Add 1 year
-- 2027-11-04 00:00:00
SELECT CURRENT_DATE + INTERVAL '1 year';

-- Subtract 3 hours
-- 2026-11-04 17:29:49.553008+05:30
SELECT NOW() - INTERVAL '3 hours';

-- subtract 2 dates
-- -2
select DATE '2026-11-10' - DATE '2026-11-12';

-- 4
select DATE '2026-11-16' - DATE '2026-11-12';
```

## AGE()

Calculates the difference between two timestamps as an interval

```sql
-- 30 years 4 mons 11 days 20:32:44.977534
SELECT AGE(
    NOW(),
    DATE '1996-06-23'
);
```