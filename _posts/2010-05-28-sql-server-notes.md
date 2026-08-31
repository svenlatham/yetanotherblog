---
layout: post
title: "SQL Server Notes"
date: 2010-05-28 12:07:00 +0000
permalink: /2010/05/28/sql-server-notes/
author: "sven"
categories: ["Uncategorized"]
---

For fans (or reluctant users) of SQL Server - here is a quick and easy way to get approximate table sizes for a database:  
`USE [dbname]  
GO  
CREATE TABLE #temp (  
table_name sysname ,  
row_count INT,  
reserved_size VARCHAR(50),  
data_size VARCHAR(50),  
index_size VARCHAR(50),  
unused_size VARCHAR(50))  
SET NOCOUNT ON  
INSERT #temp  
EXEC sp_msforeachtable 'sp_spaceused ''?'''  
SELECT a.table_name,  
a.row_count,  
COUNT(*) AS col_count,  
a.data_size  
FROM #temp a  
INNER JOIN information_schema.columns b  
ON a.table_name collate database_default  
= b.table_name collate database_default  
GROUP BY a.table_name, a.row_count, a.data_size  
ORDER BY CAST(REPLACE(a.data_size, ' KB', '') AS integer) DESC  
DROP TABLE #temp`

...and a way to list all column specs...

`USE [dbname]  
GO  
CREATE TABLE #temp (  
table_name sysname ,  
row_count INT,  
reserved_size VARCHAR(50),  
data_size VARCHAR(50),  
index_size VARCHAR(50),  
unused_size VARCHAR(50))  
SET NOCOUNT ON  
INSERT #temp  
EXEC sp_msforeachtable 'sp_spaceused ''?'''  
SELECT a.table_name,  
b.COLUMN_NAME, b.COLUMN_DEFAULT, b.IS_NULLABLE, b.DATA_TYPE, b.CHARACTER_MAXIMUM_LENGTH  
FROM #temp a  
INNER JOIN information_schema.columns b  
ON a.table_name collate database_default  
= b.table_name collate database_default  
--GROUP BY a.table_name, a.row_count, a.data_size  
ORDER BY CAST(REPLACE(a.data_size, ' KB', '') AS integer) DESC  
DROP TABLE #temp`

For this you could also `SELECT * FROM information_schema.columns`

Original code from <http://blog.sqlauthority.com/2007/01/10/sql-server-query-to-find-number-rows-columns-bytesize-for-each-table-in-the-current-database-find-biggest-table-in-database/>
