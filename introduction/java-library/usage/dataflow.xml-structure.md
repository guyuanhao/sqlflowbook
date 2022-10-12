---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/617965/file/1485427?sub_id=6439709
---

# Dataflow.xml structure

DataFlowAnalyzer will generate dataflow.xml. This page indends to describe the structure of the dataflow.xml.

### Root elements

*   table

    Belongs to the Table Structure
*   view

    Belongs to the Table Structure
*   resultset

    Belongs to the Table Structure
*   package

    Belongs to the oraclePackage Structure
*   procedure

    Includes procedure, function, trigger

    Belongs to the Procedure Structure
*   database

    Belongs to the Table Structure
*   schema

    Belongs to the Table Structure
*   stage

    Belongs to the Table Structure
*   datasource

    Belongs to the Table Structure
*   stream

    Belongs to the Table Structure
*   path

    External file

    Belongs to the Table Structure
*   variable

    Belongs to the Table Structure
*   process

    Data movement process from table A to table B generates process. Process is used to display table level relation on UI.

    Belongs to the Process Structure
*   relationship

    Analysis result

    Belongs to the Relationship Structure
*   error

    Errors during the analysis

    Belongs to the Error Structure
*   orientation&#x20;

    UI graph orientation.&#x20;

    Enumeration, types are: LEFT\_TO\_RIGHT、RIGHT\_TO\_LEFT、TOP\_TO\_BOTTOM、BOTTOM\_TO\_TOP

### Table Structure

*   id

    table id
*   server

    db server to which the table belongs
*   database

    database to which the table belongs
* schema
  * table索索schema
*   name

    table name, database.schema.table for example. if there's no database the name would be schema.table. If there's no schema the name will be database.table
*   alias

    alias name
*   uri

    mapped url when table type is file, path, stage or stream
*   type

    table type
*   subType

    subtype of the type
*   processIds

    linked process Ids
*   fileType

    mapped file type if the table type is stage
*   fileFormat

    mapped file format if table type is file, path, stage or stream
*   location

    location url if the table type is stage or datasource
*   isTarget

    if display in UI&#x20;
*   coordinate

    element coordinate
*   parent

    storage process of the table
*   more

    if collaspe in the UI

Subnode in Table structure:

*   column

    Belongs to the Column Structure

### Column Structure

### OraclePackage Structure

### Procedure Structure

### Argument Structure

### Process Structure

### Relationship Structure

### TargetColumn Structure

### SourceColumn Structure

### Transform Structure

### Error Structure

