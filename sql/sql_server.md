### SYS Tables
```sql
select top 10 * from sys.partition_functions
select top 10 * from sys.partition_range_values
select top 10 * from sys.sysusers
select top 10 * from sys.partitions
select top 10 * from sys.indexes
select top 10 * from sys.objects
```

### Who ran blocking transactions?
```sql
EXEC sp_who2

SELECT  *
FROM sys.dm_exec_requests
WHERE blocking_session_id <> 0

select * from sys.dm_tran_session_transactions

SELECT session_id, wait_duration_ms, wait_type, blocking_session_id 
FROM sys.dm_os_waiting_tasks
```

### Who has permissions?
```sql
SELECT
    princ.name,
    princ.type_desc,
    perm.permission_name,
    perm.state_desc,
    perm.class_desc,
    object_name(perm.major_id)
FROM sys.database_principals princ
LEFT JOIN sys.database_permissions perm ON perm.grantee_principal_id = princ.principal_id
WHERE name = '<user_name>'
```

### Get objects that refer view
```sql
-- 1
select * from INFORMATION_SCHEMA.VIEWS where VIEW_DEFINITION like '%actual_recoveries_vw%'
-- 2
select
    object_name(m.object_id), m.*
from
    sys.sql_modules m
where
    m.definition like N'%my_view_name%'
```

## Object definitions
```sql
select name, type_desc, definition
from sys.objects sysObj
join sys.sql_modules sqlModule on sqlModule.object_id = sysObj.object_id
-- where name = '<some_name>'
```

### Who Ran delete query?
```sql
USE ReadingDBLog
GO
SELECT 
    [Transaction ID],
    Operation,
    Context,
    AllocUnitName
    
FROM 
    fn_dblog(NULL, NULL) 
WHERE 
    Operation = 'LOP_DELETE_ROWS'

USE ReadingDBLog
GO
SELECT
    Operation,
    [Transaction ID],
    [Begin Time],
    [Transaction Name],
    [Transaction SID]
FROM
    fn_dblog(NULL, NULL)
WHERE
    [Transaction ID] = '0000:000004ce'
AND
    [Operation] = 'LOP_BEGIN_XACT'

USE MASTER
GO   
SELECT SUSER_SNAME(0x0105000000000005150000009F11BA296C79F97398D0CF19E8030000)
```

### Who ran drop?
```sql
USE ReadingDBLog
GO
SELECT 
Operation,
[Transaction Id],
[Transaction SID],
[Transaction Name],
 [Begin Time],
   [SPID],
   Description
FROM fn_dblog (NULL, NULL)
WHERE [Transaction Name] = 'DROPOBJ'
GO

SELECT SUSER_SNAME(0x0105000000000005150000009F11BA296C79F97398D0CF19E8030000) 
```

### Collation
- Collation refers to a set of rules that determine how data is sorted and compared.
- Find the collation of the current server
  - select SERVERPROPERTY ('collation')
- Find the collation of a particular database
  - select convert(sysname,DatabasePropertyEx('CS_AS_KS_WS','Collation'))
- Find the collation of the current database
  - select convert(sysname,DatabasePropertyEx(db_name(),'Collation'))
- Find collation of all columns in a table
  - select name, collation from syscolumns where [id]=object_id('Mytable')
- Find all collation available in SQL Server
  - select * from ::fn_helpcollations()
