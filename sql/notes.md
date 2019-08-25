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
Your best bet will be to use **SSIS** or **BULK INSERT**. There are various performance improvements that you can do when using them and they are very well documented in [The Data Loading Performance Guide][1].

At **SSIS** level, you can look into below things to speed up data read and data load :

 - [Fast Parse][7] Option along with its limitations.
 - Use the SQL Server Native Client 10.x OLE DB provider for an In-Memory, high performance connection
 - Set the Packet Size to 32767
 - Select the OLE DB Destination  Data Access mode “Table or View – fast load”  option 

Refer to [Speeding Up SSIS Bulk Inserts into SQL Server][8] for more details.

Below are some good ways to improve BULK INSERT operations :

 1. Using TABLOCK as query hint.
 2. Dropping Indexes during Bulk Load operation and then once it is completed then recreating them.
 3. Changing the Recovery model of database to be BULK_LOGGED during the load operation.
 4. If the target has Clustered Index then specifying ORDER BY clause in the bulk insert operation will increase the speed of BULK loading.
 5. Using Trace Flag 610 at the beginning of BULK INSERT operation.

The max degree of parallelism should be configured on the server rather than the default. You can refer to my answer on how it configure it [**here**][2].

If you are using SQL Server 2014 then [`SELECT ... INTO` is parallel][3].

Also, you should monitor **Wait Statistics** on the server especially SOS_SCHEDULER_YIELD resulting in scheduler contention on Servers having multiple CPUs running concurrent Bulk load operations and competing for the same CPU Cycles.

Also refer to :

 - [Bulk Inserting 1 Terabyte within 10 minutes][4]
 - [We Loaded 1TB in 30 Minutes with SSIS, and So Can You][5]
 - [Load 1TB in less than 1 hour][6]


  [1]: https://technet.microsoft.com/en-us/library/dd425070%28v=sql.100%29.aspx
  [2]: https://dba.stackexchange.com/questions/36522/what-is-a-good-repeatable-way-to-calculate-maxdop-on-sql-server/36578#36578
  [3]: http://sqlperformance.com/2013/08/t-sql-queries/parallel-select-into
  [4]: http://henkvandervalk.com/sql2008-r2-dce-on-a-96-core-unisys-es7000-server-with-dsi-solid-state-storage-bulk-inserting-1-terabyte-within-10-minutes
  [5]: http://msdn.microsoft.com/en-us/library/dd537533%28v=sql.100%29.aspx
  [6]: http://blogs.msdn.com/b/sqlcat/archive/2006/05/19/602142.aspx
  [7]: http://msdn.microsoft.com/en-us/library/ms139833.aspx
  [8]: http://henkvandervalk.com/speeding-up-ssis-bulk-inserts-into-sql-server
