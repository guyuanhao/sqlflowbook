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
