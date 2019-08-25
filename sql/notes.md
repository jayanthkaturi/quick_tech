### INSERT INTO VS SELECT INTO
```sql
-- New table
SELECT
  *
INTO new_table
FROM old_table
WHERE <condition_on_old_table>

-- Existing table
INSERT INTO new_table
SELECT col1, col2...
FROM old_table
WHERE <condition_on_old_table>
```

### BULK INSERT VS INSERT [(ref)](https://docs.microsoft.com/en-us/previous-versions/sql/sql-server-2008/dd425070(v=sql.100))
```
Why bulk insert is faster than insert?

1. To support high-volume data loading scenarios, SQL Server implements minimally logged operations.
Unlike fully logged operations, which use the transaction log to keep track of every row change,
minimally logged operations keep track of extent allocations and metadata changes only.
```
