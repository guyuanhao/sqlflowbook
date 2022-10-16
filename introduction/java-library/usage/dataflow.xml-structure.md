---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/617965/file/1485427?sub_id=6439709
---

# Dataflow.xml structure

This page indends to describe the structure of the dataflow.xml. DataFlowAnalyzer generates _`dataflow.xml`_ if the _`/json`_ is not set.  Response will be in json format if the _`/json`_ is set.  Please refer to [here](../../../concepts/data-lineage-format-reference.md) for the json response.&#x20;

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

*   id

    procedure id
*   server

    db server to which the procedure belongs
*   database

    database to which the procedure belongs
*   schema

    schema to which the procedure belongs
*   name

    procedure name: _`database.schema.procedure`_ The name would be : _`schema.procedure`_ If there's no database . The name would be _`database.procedure`_ if there 's no schema

    if the procedure belongs to package, full name will also contain package segment
*   type

    procedure type, could be _`procedure`_, _`function`_, _`trigger`_
*   coordinate

    procedure coordinate&#x20;

Subnode in procedure structure:

*   argument

    Belongs to the Argument Structure

### Argument Structure

Argument is to describe the parameters during the storage process

*   id

    argument id
*   name

    argument name
*   coordinate

    argument coordinate
*   datatype

    argument data type
*   inout

    in or out type

### Process Structure

Process will be generated when data flow moves from one table to another

* id
  * process id
*   server

    db server to which the process belongs
*   database

    database to which the process belongs
*   schema

    schema to which the process belongs
*   name

    process name, different process can have the same name
*   procedureName

    procedure to which the process belongs
*   procedureId

    procedure id to which the process belongs
*   queryHashId

    statement hashcode to which the process belongs
*   type

    process type
*   coordinate

    process coordinate

### Relationship Structure

Relationship will tell the data lineage relationship. It can be on table level and column level.&#x20;

Table level can be: table --> process --> table

Column level can be: column --> column

*   id

    relationship id
*   type

    relationship type: _`fdd`_, _`fdr`_, _`join`_ or _`call`_
*   function

    function name if the relationship is from a function
*   effectType

    effect type of the relationship
*   clause

    the join condtion clause type when the relationship is from join
*   joinType

    join type
*   processId

    relationship process id, which can be used to calculate table level
*   processType

    process type of the relationship
*   sqlHash

    statement hash of the relationship
*   sqlComment

    statement comment of the relationship, which is used to get extra information&#x20;
*   condition

    join condtion clause when the relationship type is _`join`_
*   timestampMin

    the earliest time when the relationship is generated
*   timestampMax

    the latest time when the relationship is generated

Subnode in the Relationship:

*   target

    Target when the relationship type is _`fdd`_, _`fdr`_, _`join`_

    Belongs to the TargetColumn Structure
*   source

    Source when the relationship type is _`fdd`_, _`fdr`_, _`join`_

    Belongs to the SourceColumn Structure
*   caller

    Caller when the relationship type is _`call`_

    Belongs to the TargetColumn Structure
*   callee

    Callee when the relationship type is _`call`_

    Belongs to the SourceColumn Structure

### TargetColumn Structure

[aaa](../../../concepts/sqlflow-data-reference.md#target-fields-data)

{% content-ref url="../../../concepts/sqlflow-data-reference.md" %}
[sqlflow-data-reference.md](../../../concepts/sqlflow-data-reference.md)
{% endcontent-ref %}

### SourceColumn Structure

*   id

    source column Id
*   name

    caller name if the Relationship type is _`call`_
* column
  * source column name
*   source\_id

    source id when the source is not on column level
*   source\_name

    source name when the source is not on column level
*   column\_type

    column type
*   parent\_id

    source parent node id&#x20;
*   parent\_name

    source parent node name
*   parent\_alias

    source parent node alias
* coordinate
*   clauseType

    source clause type
*   source

    will be filtered out on UI if the source is from system
*   type

    type of the storage process if the Relationship type is _`call`_. could be: _`procedure`_, _`function`_, _`trigger`_, _`macro`_

subnode in the SourceColumn&#x20;

*   transforms

    Belongs to the Transform Structure

### Transform Structure

Describe how the Relationship is generated

*   type

    type, could be: _`simple`_, _`function`_, _`expression`_, _`constant`_, _`case`_ or _`subquery`_
* coordinate
*   code

    code expression

### Error Structure

Errors during the analysis

* errorMessage
*   errorType

    error type, could be: _`SyntaxError`_, _`SyntaxHint`_, _`AnalyzeError`_, _`LinkOrphanColumn`_
*   coordinate

    coordinate where errors happen
*   file

    sql file information of the errors
*   originCoordinate

    original coordinate where errors happen
