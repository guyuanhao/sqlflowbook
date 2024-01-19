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

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### XMLCOLATTVAL（value\_expr\[,value\_expr2],...)

This function is used to generate an XML block, and the parameter value\_expr is used to specify the column name or alias as the attribute name.

```sql
SELECT xmlelement ("emp",xmlcolattval (ename,sal)) xml FROM emp WHERE DEPTNO = 10;
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### SYS\_DBURIGEN({column|attribute})

`SYS_DBURIGen` takes as its argument one or more columns or attributes, and optionally a rowid, and generates a URL of data type `DBURIType` to a particular column or row object. You can then use the URL to retrieve an XML document from the database.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_DBURIGEN.html#GUID-ABA33BEB-F7B7-477B-9FF2-028D62768797](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_DBURIGEN.html#GUID-ABA33BEB-F7B7-477B-9FF2-028D62768797)

```sql
SELECT sys_dburigen(ename) url FROM emp WHERE deptno=10;
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### SYS\_XMLAGG（expr\[，fmt]）

`SYS_XMLAgg` aggregates all of the XML documents or fragments represented by `expr` and produces a single XML document. It adds a new enclosing element with a default name `ROWSET`. If you want to format the XML document differently, then specify `fmt`, which is an instance of the `XMLFormat` object.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_XMLAGG.html#GUID-BEDD241D-360A-46A2-AEBF-C8B70E465D75](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_XMLAGG.html#GUID-BEDD241D-360A-46A2-AEBF-C8B70E465D75)

```sql
SELECT SYS_XMLAGG(SYS_XMLGEN(ename))  xml_content FROM emp;
```

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### SYS\_XMLGEN(expr\[,fmt])

`SYS_XMLGen` takes an expression that evaluates to a particular row and column of the database, and returns an instance of type `XMLType` containing an XML document. The `expr` can be a scalar value, a user-defined type, or an `XMLType` instance.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_XMLGEN.html#GUID-1AC25984-F4AB-468E-BF53-561275AD44E8](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/SYS\_XMLGEN.html#GUID-1AC25984-F4AB-468E-BF53-561275AD44E8)

```sql
SELECT sys_xmlgen(ename) xml FROM emp WHERE deptno=10;
```

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### XMLAGG（XMLType\_instance\[ORDER BY sort\_list])

This function is used to aggregate multiple XML fragment and generate an XML document. The parameter XMLType\_instance is used to specify the XMLType instance, and sort\_list is used to generate the specified sorting method.

```sql
SELECT xmlagg(xmlelement("employee",ename||' '||sal))  xml FROM emp WHERE deptno=10;
```

<figure><img src="../.gitbook/assets/图片.png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/图片 (1).png" alt=""><figcaption></figcaption></figure>

### XMLELEMENT(identifier\[,xml\_attribute\_clause]\[,value\_expr])

`XMLElement` takes an element name for `identifier` or evaluates an element name for `EVALNAME` `value_expr`, an optional collection of attributes for the element, and arguments that make up the content of the element. It returns an instance of type `XMLType`. `XMLElement` is similar to `SYS_XMLGen` except that `XMLElement` can include attributes in the XML returned, but it does not accept formatting using the `XMLFormat` object.\
[https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/XMLELEMENT.html#GUID-DEA75423-00EA-4034-A246-4A774ADC988E](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/XMLELEMENT.html#GUID-DEA75423-00EA-4034-A246-4A774ADC988E)

```sql
select xmlelement ("DATE",sysdate)  from dual;
```

<figure><img src="../.gitbook/assets/图片 (2).png" alt=""><figcaption></figcaption></figure>

Result:

<figure><img src="../.gitbook/assets/图片 (21).png" alt=""><figcaption></figcaption></figure>