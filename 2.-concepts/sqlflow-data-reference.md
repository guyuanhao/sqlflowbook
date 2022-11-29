# SQLFlow Data Reference

### Target Fields Data

*   id

    id of the target column&#x20;
*   name

    name of the target column. the name would be the caller if the Relationship type is _`call`_&#x20;
*   column

    column name
*   function

    fucntion name if the relationship is from a function
*   target\_id

    target id if the target is not on column level
*   target\_name

    target name if the target is not on column level
*   parent\_id

    parent id of the target's parent node
*   parent\_name

    parent name of the target's parent node
*   parent\_alias

    parent alias of the target's parent node
* coordinate
*   source

    will be filtered out on UI if the source is from system
*   type

    type of the storage process if the Relationship type is _`call`_. could be: _`procedure`_, _`function`_, _`trigger`_, _`macro`_

### Source Fields Data

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

### Transform Fields Data

Describe how the Relationship is generated

*   type

    type, could be: _`simple`_, _`function`_, _`expression`_, _`constant`_, _`case`_ or _`subquery`_
* coordinate
*   code

    code expression

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

    mapped file format if table type is \`\`\` `_`file, path, stage`_ or _`stream\`\_
*   location

    location url if the table type is _`stage` or `datasource`_
*   isTarget

    if display in UI
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

    column source. will not be dispalyed If source is _`system`_
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

    package coordinate

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

    procedure coordinate

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
