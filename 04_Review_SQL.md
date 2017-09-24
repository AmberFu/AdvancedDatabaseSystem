# Relational Algebra 
* SELECT operator： ( σ conditions... Relation)
    * pick rows
* PROJECT operator： ( π attributes Relation)
    * pick columns
* COMPOSE operator：
    * pick rows then columns 
    => π attribute1, attribute2 ( σ conditions... Relation )
* CROSS-PRODUCT： (a.k.a Cartesian Product) R1 X R2
    * If R1 has n-tuple and R2 has m-tuple, then R1 X R2 will have n * m tuples.
* NATURAL JOIN：(⋈)   
    * 強制合併相同名稱的 attribute
    * 消去重複名稱的 attribute
* Theta join： (θ)
    * 一般的 join 一般指此項

# SQL (SEQUELXRM)
* History：
    * 1986 SQL-86 (SQL-1)
    * 1992 SQL-92 (SQL-2)
    * 1999 SQL-3 : 
        * DML ( Data Manipulstion Language )
        * DDL ( Data Definition Language )
    * 2003 : add XML-related feature
    * 2006 : can be used with XML
    * 2008 : add ORDER BY outside cursor, INSTED OF triggers, TRUNCATE statement, FETCH clause
    * 2011 : add PERIOD FOR ...
    * 2016 : add JSON, row pattern matching, ...
* DML :
    * Query：
        SELECT : * or attribute name
        FROM : relation，不一定要是 Table ( input/ output are a relation )
        WHERE : 包含比較運算子 { =, <>, >, <, >=, <= } 及 boolean combination {AND, OR, NOT }
        ORDER BY : ASC, DESC
        GROUP BY : group some attribute ( must also in SELECT statement)
        HAVING : 限制前面 GROUP 結果

    * combine / JOIN : 
        * INNER JOIN
        * OUTER JOIN : In Oracle, place (+) on secondary table in WHERE statement.
            * LEFT (OUTER) JOIN
            * RIGHT (OUTER) JOIN
        * UNION
        * INTERSECT
        * MINUS
    * set membership operator / IN or NOT IN : 可篩選一整組的值
    * set comparison operators / CONTAINS, SOME, ANY, ALL : output 是 Ture / False
        * CONTAINS : A CONTAINS B == set A is a superset of set B
        * SOME :
        * ANY :
        * ALL :
    * Aggregation Functions : result will be single value
        * COUNT([DISTINCT] x)
        * SUM([DISTINCT] x)
        * AVG([DISTINCT] x)
        * MAX(x)
        * MIN(x)
    * ISERT :
    * DELETE :
    * UPDATE :
    * VIEW :
* DDL :
    * CREATE TABLE :
    * ALTER TABLE :
    * DROP TABLE :
    * CREATE INDEX :
