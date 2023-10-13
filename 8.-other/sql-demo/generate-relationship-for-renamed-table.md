# Generate relationship for renamed table

A table can be renamed by using a system procedure in SQLServer/AzureSQL called sp\_rename. In the following sample procedure, a table gets renamed from `EmployeeSales` to `FactEmployeeSales` followed by INSERT from the renamed table:

````plsql
```
CREATE TABLE dbo.EmployeeSales
(
    DataSource varchar(20) NOT NULL,
    BusinessEntityID varchar(11) NOT NULL,
    LastName varchar(40) NOT NULL,
    SalesDollars money NOT NULL
);

CREATE PROCEDURE dbo.uspUpdateEmployeeSales
AS
    SET NOCOUNT ON;

    EXEC sp_rename 'dbo.EmployeeSales', 'FactEmployeeSales';

    INSERT INTO dbo.AggSales
    SELECT LastName, SUM(SalesDollars) AS [Agg Sales]
    FROM dbo.FactEmployeeSales
    GROUP BY LastName;
```
````

Result:

<figure><img src="../../.gitbook/assets/图片.png" alt=""><figcaption></figcaption></figure>
