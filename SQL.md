#SQL#

#MS SQL#

Truncate all tables in a database [ MS SQL]

    -- disable all constraints
    EXEC sp_msforeachtable "ALTER TABLE ? NOCHECK CONSTRAINT all"

    -- delete data in all tables
    EXEC sp_MSForEachTable "DELETE FROM ?"

    -- enable all constraints
    exec sp_msforeachtable "ALTER TABLE ? WITH CHECK CHECK CONSTRAINT all"

#MySQL#
