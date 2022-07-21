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


