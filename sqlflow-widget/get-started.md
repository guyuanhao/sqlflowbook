---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/doc/widget/readme.md#2-get-started
---

# Get started

The SQLFlow widget is a Javascript library that enables instantaneous data lineage visualisation on your website.

The SQLFlow widet must work together with the Gudu SQLFlow backend in order to visualize the data lineage and provides an actionable diagram.

The SQLFlow widget is shipped together with [the SQLFlow On-Premise version](https://www.gudusoft.com/sqlflow-on-premise-version/).&#x20;

Once the SQLFlow widget is installed on your server, you can access the SQLFlow widget with the url such as: [https://127.0.0.1/widget](https://127.0.0.1/widget). Currently there are no online demos available.

<figure><img src="../.gitbook/assets/SQL-Metadata-Sources_700_988_white-600x847.png" alt=""><figcaption></figcaption></figure>

* Visualize the lineage of the SQL queries.
* Show specific table/column lineage graphics on the web page.
* Package the data lineage into a standalone web app.
* Shipped together with the [SQLFlow On-Premise](https://www.gudusoft.com/sqlflow-on-premise-version/) version.

\
\
**Files**

```
├── index.html
├── index.js
├── sqlflow.widget.2.4.9.css
└── sqlflow.widget.2.4.9.js
```

> Please note that the version number in the file will changed constantly.

Add `sqlflow.widget.2.4.9.js` in index.html, during the execution of the JS, a new iframe will be created, and the css from js will be embedded into the iframe, no additional css is needed.

jquery is optional, and is inlcuded for the demostration only.

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>widget</title>
        <script src="https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js"></script>
        <script src="sqlflow.widget.2.4.9.js"></script>
        <script src="index.js"></script>
    </head>

    <body>
        <div id="sqlflow"></div>
    </body>
</html>
```

Insert the following code in index.js:

```js
$(async () => {
    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 315,
        apiPrefix: 'http://101.43.8.206/api',
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    // set sql text property
    sqlflow.sqltext.set(`CREATE VIEW vsal 
    AS 
      SELECT a.deptno                  "Department", 
             a.num_emp / b.total_count "Employees", 
             a.sal_sum / b.total_sal   "Salary" 
      FROM   (SELECT deptno, 
                     Count()  num_emp, 
                     SUM(sal) sal_sum 
              FROM   scott.emp 
              WHERE  city = 'NYC' 
              GROUP  BY deptno) a, 
             (SELECT Count()  total_count, 
                     SUM(sal) total_sal 
              FROM   scott.emp 
              WHERE  city = 'NYC') b 
    ;`);

    sqlflow.visualize();
});
```

You can find the execution result here: [demo：visualize sqltext](http://101.43.8.206/widget/1/#/)

#### Parameter

| name      | detail                                                                             | type             | optional |
| --------- | ---------------------------------------------------------------------------------- | ---------------- | -------- |
| container | the html element where sqlflow is attached                                         | HTMLElement      | no       |
| apiPrefix | the url of sqlflow backend                                                         | string           | no       |
| width     | width of container, both percent and fix length can be used like "100%", or 800px  | string \| number | no       |
| height    | height of container, both percent and fix length can be used like "100%", or 800px | string \| number | no       |
