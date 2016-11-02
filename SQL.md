#SQL#

Finding Table with more than 1 entry

    SELECT 
     <column_name> ,
     COUNT(*) count
    FROM 
     <Table_Name>
    GROUP BY
     <column_name>
    Having
    COUNT(*) > 1

#MS SQL#

Truncate all tables in a database [ MS SQL]

    -- disable all constraints
    EXEC sp_msforeachtable "ALTER TABLE ? NOCHECK CONSTRAINT all"

    -- delete data in all tables
    EXEC sp_MSForEachTable "DELETE FROM ?"

    -- enable all constraints
    exec sp_msforeachtable "ALTER TABLE ? WITH CHECK CHECK CONSTRAINT all"

#MySQL#
