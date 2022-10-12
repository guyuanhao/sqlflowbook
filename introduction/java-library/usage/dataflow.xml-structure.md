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

    Enumeration, types are: _`LEFT_TO_RIGHT、RIGHT_TO_LEFT、TOP_TO_BOTTOM、BOTTOM_TO_TOP`_

### Table Structure

*   id

    table id
*   server

    db server to which the table belongs
*   database

    database to which the table belongs
* schema
  * table schema
*   name

    table name, _`database.schema.table`_ for example. if there's no database the name would be _`schema.table`_. If there's no schema the name will be _`database.table`_
*   alias

    alias name
*   uri

    mapped url when table type is _`file, path, stage`_ or _`stream`_
*   type

    table type
*   subType

    subtype of the type
*   processIds

    linked process Ids
*   fileType

    mapped file type if the table type is _stage_
*   fileFormat

    mapped file format if table type is ``` `_`file, path, stage`_ or _`stream`_
*   location

    location url if the table type is _`stage` or `datasource`_
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

* id
  * column id
* name
  * column name
* coordinate
  * column coordinate
*   source

    column source. will not be dispalyed If source is _`system`_&#x20;
* qualifiedTable
  * Field which is used to distinguish the column when there are columns under the same name such as: table1.a, table2.a

### OraclePackage Structure

*   id

    package id
*   server

    db server to which the package belongs
*   database

    database to which the package belongs
*   schema

    schema to which the package belongs
*   name

    package name: _`database.schema.package`_ The name would be : _`schema.package`_ If there's no database . The name would be _`database.package`_ if there 's no schema.
*   type

    package type
*   coordinate

    package coordinate&#x20;

Subnode in OraclePackage structure:

*   procedure

    Belongs to the Procedure Structure

### Procedure Structure

### Argument Structure

### Process Structure

### Relationship Structure

### TargetColumn Structure

### SourceColumn Structure

### Transform Structure

### Error Structure

