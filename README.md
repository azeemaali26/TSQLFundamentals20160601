# TSQLFundamentals_20160601

#T-SQL语句逻辑处理顺序：

FROM

WHERE

GROUP BY

HAVING

SELECT

  表达式

  DISTINCT

ORDER BY

  TOP / OFFSET-FETCH



#运算符优先级：

()

*, /, %

+(正号), -(负号), +(加号), +(串联), -(减号)

=(等号), >, <, >=, <=, !=, !>, !<

NOT

AND

OR, BETWEEN, IN, LIKE

=(赋值)



#CASE表达式的等价缩写：

COALESCE() --标准函数，推荐使用

ISULL() --非标准函数，不推荐使用，COALESCE()等价，参数更丰富

IIF() --非标准函数，SQL 2012版本以上，更好的支持从Access迁移

CHOOSE() --非标准函数，SQL 2012版本以上，更好的支持从Access迁移



#Sample:

OFFSET-FETCH:

SELECT orderid, orderdate, custid, empid
FROM Sales.Orders
ORDER BY orderdate, orderid
OFFSET 50 ROWS FETCH NEXT 25 ROWS ONLY;


开窗函数：
SELECT orderid, custid, val,
  ROW_NUMBER() OVER(PARTITION BY custid
                    ORDER BY val) AS rownum
FROM Sales.OrderValues
ORDER BY custid, val;



