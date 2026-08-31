---
layout: post
title: "Copy Database in SQL Server 2008"
date: 2010-07-23 06:29:22 +0000
permalink: /2010/07/23/copy-database-in-sql-server-2008/
author: "sven"
categories: ["Uncategorized"]
---

You want to copy a database, maybe for development purposes? Try this: It is based on [this code by Michael Schwarz](http://weblogs.asp.net/mschwarz/archive/2004/08/26/220735.aspx), but updated for SQL Server 2008:  
`USE master  
GO  
-- the original database (use 'SET @DB = NULL' to disable backup)  
DECLARE @DB varchar(200)  
SET @DB = ''  
-- the backup filename  
DECLARE @BackupFile varchar(2000)  
SET @BackupFile = 'c:\temp\backup.dat'  
-- the new database name  
DECLARE @TestDB varchar(200)  
SET @TestDB = 'MydatabaseDevelopment'  
-- the new database files without .mdf/.ldf  
DECLARE @RestoreFile varchar(2000)  
SET @RestoreFile = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.SQLEXPRESS\MSSQL\DATA\MydatabaseDevelopment'  
-- ****************************************************************  
-- no change below this line  
-- ****************************************************************  
DECLARE @query varchar(2000)  
DECLARE @DataFile varchar(2000)  
SET @DataFile = @RestoreFile + '.mdf'  
DECLARE @LogFile varchar(2000)  
SET @LogFile = @RestoreFile + '.ldf'  
IF @DB IS NOT NULL  
BEGIN  
SET @query = 'BACKUP DATABASE ' + @DB + ' TO DISK = ' + QUOTENAME(@BackupFile, '''')  
EXEC (@query)  
END  
-- RESTORE FILELISTONLY FROM DISK = 'C:\temp\backup.dat'  
-- RESTORE HEADERONLY FROM DISK = 'C:\temp\backup.dat'  
-- RESTORE LABELONLY FROM DISK = 'C:\temp\backup.dat'  
-- RESTORE VERIFYONLY FROM DISK = 'C:\temp\backup.dat'  
IF EXISTS(SELECT * FROM sysdatabases WHERE name = @TestDB)  
BEGIN  
SET @query = 'DROP DATABASE ' + @TestDB  
-- EXEC (@query)  
END  
RESTORE HEADERONLY FROM DISK = @BackupFile  
DECLARE @File int  
SET @File = @@ROWCOUNT  
DECLARE @Data varchar(500)  
DECLARE @Log varchar(500)  
SET @query = 'RESTORE FILELISTONLY FROM DISK = ' + QUOTENAME(@BackupFile , '''')  
CREATE TABLE #restoretemp  
(  
LogicalName varchar(500),  
PhysicalName varchar(500),  
type varchar(10),  
FilegroupName varchar(200),  
size int,  
maxsize bigint,  
x1 nvarchar(1),  
x2 nvarchar(1),  
x3 nvarchar(1),  
x4 uniqueidentifier,  
x5 int,  
x6 int,  
x7 bigint,  
x8 int,  
x9 int,  
x10 nvarchar(1),  
x11 bigint,  
x12 uniqueidentifier,  
x13 int,  
x14 int,  
x15 nvarchar(1)  
)  
INSERT #restoretemp EXEC (@query)  
SELECT @Data = LogicalName FROM #restoretemp WHERE type = 'D'  
SELECT @Log = LogicalName FROM #restoretemp WHERE type = 'L'  
PRINT @Data  
PRINT @Log  
TRUNCATE TABLE #restoretemp  
DROP TABLE #restoretemp  
IF @File > 0  
BEGIN  
SET @query = 'RESTORE DATABASE ' + @TestDB + ' FROM DISK = ' + QUOTENAME(@BackupFile, '''') +  
' WITH MOVE ' + QUOTENAME(@Data, '''') + ' TO ' + QUOTENAME(@DataFile, '''') + ', MOVE ' +  
QUOTENAME(@Log, '''') + ' TO ' + QUOTENAME(@LogFile, '''') + ', FILE = ' + CONVERT(varchar, @File)  
EXEC (@query)  
END  
GO`  
Usual caveats apply, backup before running, etc.
