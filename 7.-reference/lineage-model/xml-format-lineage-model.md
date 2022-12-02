# XML Format Lineage Model

This page indends to describe the structure of the **dataflow.xml**. Dlineage tool generates **dataflow.xml** if the _`/json`_ is not set. Response will be in json format if the _`/json`_ is set. Please refer to [here](json-format-lineage-model.md) for the json response.

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
*   orientation

    UI graph orientation.

    Enumeration, types are: _`LEFT_TO_RIGHT、RIGHT_TO_LEFT、TOP_TO_BOTTOM、BOTTOM_TO_TOP`_

### Table Structure

{% content-ref url="sqlflow-data-reference.md#table-structure" %}
[#table-structure](sqlflow-data-reference.md#table-structure)
{% endcontent-ref %}

Subnode in Table structure:

*   column

    Belongs to the Column Structure

### Column Structure

{% content-ref url="sqlflow-data-reference.md#column-structure" %}
[#column-structure](sqlflow-data-reference.md#column-structure)
{% endcontent-ref %}

### OraclePackage Structure

{% content-ref url="sqlflow-data-reference.md#oraclepackage-structure" %}
[#oraclepackage-structure](sqlflow-data-reference.md#oraclepackage-structure)
{% endcontent-ref %}

Subnode in OraclePackage structure:

*   procedure

    Belongs to the Procedure Structure

### Procedure Structure

{% content-ref url="sqlflow-data-reference.md#procedure-structure" %}
[#procedure-structure](sqlflow-data-reference.md#procedure-structure)
{% endcontent-ref %}

Subnode in procedure structure:

*   argument

    Belongs to the Argument Structure

### Argument Structure

{% content-ref url="sqlflow-data-reference.md#argument-structure" %}
[#argument-structure](sqlflow-data-reference.md#argument-structure)
{% endcontent-ref %}

### Process Structure

{% content-ref url="sqlflow-data-reference.md#process-structure" %}
[#process-structure](sqlflow-data-reference.md#process-structure)
{% endcontent-ref %}

### Relationship Structure

Relationship will tell the data lineage relationship. It can be on table level and column level.

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

    statement comment of the relationship, which is used to get extra information
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

{% content-ref url="sqlflow-data-reference.md#target-fields-data" %}
[#target-fields-data](sqlflow-data-reference.md#target-fields-data)
{% endcontent-ref %}

### SourceColumn Structure

{% content-ref url="sqlflow-data-reference.md#sourcecolumn-structure" %}
[#sourcecolumn-structure](sqlflow-data-reference.md#sourcecolumn-structure)
{% endcontent-ref %}

subnode in the SourceColumn

*   transforms

    Belongs to the Transform Structure

### Transform Structure

{% content-ref url="sqlflow-data-reference.md#transform-fields-data" %}
[#transform-fields-data](sqlflow-data-reference.md#transform-fields-data)
{% endcontent-ref %}

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
