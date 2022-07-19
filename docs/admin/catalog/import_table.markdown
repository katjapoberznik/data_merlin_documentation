---
layout: default
title: Import table
nav_order: 1
has_children: true
parent: Catalog
grand_parent: Admin
permalink: /docs/admin/catalog
---

In order for Data Merlin to gain its automation capabilities, we must define metadata of our source and target tables, but before that, we must import them to the catalog. It should be pointed out, that most of the time, only target tables need to be imported manually, while source tables are found and imported automatically, based on parsed mapping SQL. We will dig into that part later.

1.	First, select database connection, from which you want to import one or more tables. After that, list of tables will be populated.
![](../../../snapshots/import_table_1.png)

2.	In tables list, select ones you want to import and click appropriate import button- 'Do not overwrite' means table import will be skipped for those already present in the catalog.
![](../../../snapshots/import_table_2.png)
