---
layout: default
title: Mappings
nav_order: 1
has_children: true
---

## MAPPINGS
Mapping is a central object for Data Merlin’s ETL automation process. Each of them contains a complete blueprint to load one target table. 
Process consist of three main steps:

1.	Select data from source, using SQL query
2.	Define fields selected from source to target fields
3.	Generate job

It should be noted, that multiple mappings can load data into one target table. Data flow starts with source table and ends with target table- both can be located anywhere in our system. They can even be at the same location, for example when we want to fill a dimension, with an aggregated data from another dimension. In that case, both tables are in target model.
In picture below, some of the possibilities are presented:

![](../../snapshots/mappings_1.png)

### List of Mappings

As we said before, mapping is a main document or object in Data Merlin, so is list of mappings a main form and it opens right after successful login. It is where we manage and perform operations over mappings, such as create, edit, delete, deploy and so on. 
Below, we will try to cover the most important features. Some of the options can be selected on one mapping specifically, while for others, we can mark multiple mappings, as shown on picture below.

![](../../snapshots/mappings_2.PNG)

#### 1. Create new

Opens an empty mapping details form, where we can create new mapping. More on this is covered in section below.

#### 2. Edit

Opens a mapping details form, where we can edit a mapping. More on this is covered in section below.

#### 3. Delete

Deletes all selected mappings.

#### 4. Copy

Creates exact copy of a selected mapping. It should be noted, that only user defined attributes are copied to a new mapping and we still need to parse our SQL query and generate job, for object to be created. What exactly those two operations are, will be covered in sections below.

#### 5. Catalog

Shortcut to the tables catalog, where all imported tables are listed.

#### 6.	Lock/Unlock

Before an update of a mapping is made, application tries to lock it and fails if it has already been locked by other users. 
In case, when session was aborted, while working on a mapping, other users need to manually unlock it in order to use it. This is made by selecting a mapping or more of them and select unlock button. Same goes for manual locking.

#### 7.	Deploy and report

These options are a legacy and are used on older projects. They are about to be removed in following releases. Alternatives for them can be found in “Utils” dropdown menu, but we will cover this topic below.

#### 8. Folders

Every mapping has its location folder structure defined. With this option we can arrange the structure and see which mappings certain folder contains.

#### 9. Utils

<img src="../../snapshots/mappings_3.PNG" width="200">

##### 9.1. Generate&Load

##### 9.2	Deploy script

<img src="../../snapshots/mappings_4.PNG" width="500">

##### 9.3	Report folder

##### 9.4-9.13 DOPOLNI

### Create/Edit Mappings

In this section we will show how to use mapping details form. Every tab in this form will be covered below.
In order to apply changes, we are making in our mappings, “Update” button needs to be clicked.
It is important to know, that mappings with PRODUCTION status (more on mapping statuses is covered below) have “Update” button enabled only for admin user.

<img src="../../snapshots/mappings_5.PNG" width="250">

### Basic Info

<img src="../../snapshots/mappings_6.PNG" width="700">

#### 1. Mapping name

Unique mapping name. Usually derived from a target table name.

#### 2. Description

Mapping description.

#### 3. Mapping status

Indicates in which status current mapping is. It can be set manually. Statuses like DEVELOP and TEST are just an information and they don’t influence the mapping, while PRODUCTION status disables an UPDATE button for all users except admin. This status can be set automatically, after you generate a deploy script for a certain mapping. This is option is helpful for maintaining consistency among development and production environments, when changes can be performed only when mapping is moved out of the production status.

#### 4. Folder

This attribute helps us to organize our mappings into folder tree structure. User folders are created automatically for each use we create, while rest of the structure can be managed in “List of mappings” form, with selecting “Folders” button. More on that is written in above section.

#### 5. Business tag

We can set different tags to our mappings, which can be later used in “List of mappings” to filter on desired tags. Multiple tags can be selected when filtering.

#### 6. Model type


#### 7. Mapping type

Most important attribute in basic info is mapping type. Different methodology is used in background, based on that option. We can add and implement our own custom mapping type or edit existing one- depends on target database model we are using.

<img src="../../snapshots/mappings_7.PNG" width="550">

**For dimensions:** <br>
DIMENSION – read from source
DIMENSION_COMPARE_FLDS - field compare instead of hash compare 
DIMENSION_FROM_DWH – read from DWH
DIMENSION_FROM_STG - read from ST
DIMENSION_OPEN_DELETE –Not closing record - all records are open.   
DIMENSION_PLAIN - talking SID (no sequence) 

**For facts:** <br>
FACT - read from source
FACT_FROM_STG - read from ST

**For ST tables:** <br>
MERGE – fore MERGE table
STG_TO_STG - read from ST and write to ST table 
SRC_TO_STG - read from source, write to ST table


#### 8. Target databse

As a name suggest, target database selected here.

#### 9. Target table

Just like database, target table is selected as well.

#### 10. Source database

It defines which source connection should be default, while we can use many different source connections in one mapping- we call that a FADARATED QUERY. Main advantage is, that for default connection, we don’t need to write the whole path of tables every time in our mapping SQL, but can simply define table name and schema if needed, while for other connections, we need to define connection first, than schema and table name at the end, for example: MY_SRC_CONN.dbo.MY_TABLE.

### SQL

<img src="../../snapshots/mappings_8.PNG" width="700">
Insert query and click on Generate fields. If query is ok (use just schema and table name, NOT DATABASE!). If query is ok, query fields will appear.

#### SQL editor

<img src="../../snapshots/mappings_9.PNG" width="600">

Here where we copy or write down our mapping SQL query. It is simply a query, which gives us desired data for our target table.
It is possible to extend the text editor, by clicking on three vertical lines button, between the editor and the list of fields.
Editor divides into SQL and VM tabs. The latter is generated automatically, when SQL query is parsed (by clicking “Generate fields” button- more on that is covered below). VM is a query that will be used, when populating dimensions or facts, so original source tables are replaced with the staged ones. 
Important to remember:

