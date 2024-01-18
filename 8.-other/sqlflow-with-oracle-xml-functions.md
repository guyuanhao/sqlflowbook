# SQLFlow with Oracle XML functions

### UPDATEXML（XMLType\_instance,Xpath\_string,value\_expr)

`UPDATEXML` takes as arguments an `XMLType` instance and an XPath-value pair and returns an `XMLType` instance with the updated value. If `XPath_string` is an XML element, then the corresponding `value_expr` must be an `XMLType` instance. If `XPath_string` is an attribute or text node, then the `value_expr` can be any scalar data type. You can specify an absolute `XPath_string` with an initial slash or a relative `XPath_string` by omitting the initial slash. If you omit the initial slash, then the context of the relative path defaults to the root node.\
[https://docs.oracle.com/en/database/oracle/oracle-database/12.2/sqlrf/UPDATEXML.html#GUID-55FE0EE5-6148-4934-947E-B9693AC32EF1](https://docs.oracle.com/en/database/oracle/oracle-database/12.2/sqlrf/UPDATEXML.html#GUID-55FE0EE5-6148-4934-947E-B9693AC32EF1)

```sql
UPDATE xmltable p SET p=UPDATEXML(value (p), '/PurchaseOrder/Actions/User/text() ','SCOTT');
```

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

### EXISTSNODE（XMLType\_instance，Xpath\_string）

`EXISTSNODE` determines whether traversal of an XML document using a specified path results in any nodes. It takes as arguments the `XMLType` instance containing an XML document and a `VARCHAR2` XPath string designating a path. The optional `namespace_string` must resolve to a `VARCHAR2` value that specifies a default mapping or namespace mapping for prefixes, which Oracle Database uses when evaluating the XPath expression(s).\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/EXISTSNODE.html](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/EXISTSNODE.html)

```sql
SELECT existsnode(VALUE(p),'/PurchaseOrder/Actions/User') node  FROM xmltable p;
```

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

### EXTRACT（XMLType\_instance，Xpath\_string）

This function is used to return the corresponding content under the XML node path. The parameter XMLType\_instance is used to specify the XMLType instance, and Xpath\_string is used to specify the XML node path.

```sql
SELECT extract(value (p),'/PurchaseOrder/Actions/User') content  FROM xmltable p;
```

Result:

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

### EXTRACTVALUE（XMLType\_instance,Xpath\_string)

The `EXTRACTVALUE` function takes as arguments an `XMLType` instance and an XPath expression and returns a scalar value of the resultant node. The result must be a single node and be either a text node, attribute, or element. If the result is an element, then the element must have a single text node as its child, and it is this value that the function returns. You can specify an absolute `XPath_string` with an initial slash or a relative `XPath_string` by omitting the initial slash. If you omit the initial slash, the context of the relative path defaults to the root node.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/EXTRACTVALUE.html#GUID-20AB974B-7544-4F44-B539-787FB6145680](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/EXTRACTVALUE.html#GUID-20AB974B-7544-4F44-B539-787FB6145680)

```sql
SELECT extractvalue(value(p),'/PurchaseOrder/Actions/User')  data  FROM xmltable  p;
```

Result:

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

### XMLCONCAT（XMLType\_instance1\[,XMLType\_instance2],...)

XMLConcat takes as input a series of XMLType instances, concatenates the series of elements for each row, and returns the concatenated series. XMLConcat is the inverse of XMLSequence.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/XMLCONCAT.html#GUID-CEEEF777-4C7D-41E4-9F69-69DE6D1B07C2](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/XMLCONCAT.html#GUID-CEEEF777-4C7D-41E4-9F69-69DE6D1B07C2)

```sql
SELECT xmlconcat(xmlelement("ename", EMP.ENAME), xmlelement("sal", EMP.SAL)) xml FROM EMP WHERE EMP.DEPTNO =10;
```

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
