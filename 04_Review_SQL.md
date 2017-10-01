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
    * set comparison operators / CONTAINS, SOME, ANY, ALL : output 是 Boolean (Ture / False)
        * CONTAINS : A CONTAINS B == set A is a superset of set B
>           ex: Dept   DNo| dName |marName|floor
>                      Eng|English|  Lin  |  2
>           => Name of employees who manage all the department on the 2nd floor?
>           SELECT d1.mgrName
>           FROM Dept d1
>           WHERE ( SELECT d2.dName FROM Dept d2
>                   WHERE d1.mgrName = d2.mgrName )
>                 contains
>                 ( SELECT dName FROM Dept WHERE floor = 1 )

        * SOME :
        
        * ANY :
        
        * ALL :
        
>        ex: Employee  ID|Name|Sex|Dept|Salary
>                      12|Wang| F | CS |60,000
>            Dept      DNo|floor
>                       CS|  1
>        => Fine the name of Employees whose salary is higher than the salaey of everyone on the first floor
>        Ans1:
>        SELECT Name
>        FROM Employee
>        WHERE Salary > ALL ( SELECT e.Salary FROM Employee e, Dept d
>                             WHERE e.Dept = d.DNo and d.floor = 1 )
>        Ans2:
>        SELECT Name
>        FROM Employee
>        WHERE Salary > ( SELECT max(e.Salary) FROM Employee e, Dept d
>                         WHERE e.Dept = DNo and d.floor = 1 )
>        

    * Aggregation Functions : result will be single value
        * COUNT([DISTINCT] x)
        * SUM([DISTINCT] x)
        * AVG([DISTINCT] x)
        * MAX(x)
        * MIN(x)
    * GROUP BY : group attributes MUST in SELECT place
    * HAVING : can use Aggregation Functions!
    * ISERT : INSERT INTO table VALUES value_list(a,b,c,d); <-- insert by order!
    * DELETE : DELETE table WHERE (...);
    * UPDATE : UPDATE table SET attribute WHERE (...);
    * VIEW : create a pseudo table for other people to query. 並不實際存在(physical exist)資料庫中。
         * Syntax: CREATE VIEW <view_name> AS <query-expression>
         
* DDL : 依 DBMS 差異而不同，check your DBMS first!
    * CREATE TABLE :
    * ALTER TABLE :
    * DROP TABLE :
    * CREATE INDEX : 提昇效能最主要的方式 (https://www.youtube.com/watch?v=Y7Qlc7f_u0o)
        * 資料庫在 search 時，通常會 scan 整張 table 找出 target values；但當建立 index 時,資料庫可值透過 index 直接找到 target values。（因此設定最常查詢的 attribute 為 index 非常重要）
        * Underlying (基本的) data structure
            * Balanced tree ( B tree / B+ tree ) : 有序的(?!), 0 < a <= 12 or a = 'xxx'
            * hash tables : 一對一關係，a = 'xxx'
        * Downside (不利) of INDEX :
            * Extra space
            * Index creation
            * Index maintenance
        * Picking which Indexes to create :
            * 建立 index 的好處，依據以下幾點判斷：
                * Size of table (and possibly layout)
                * Data distribution
                * Query or update load : 每次 update 後，都需要重建 index
            * Physical design advisors 實體設計的建議 :
                * Input : database (statistic) and workload
                * Output : recommended indexes
                * Query Optimizer - 考量 : 1) database statistic 2) query or update 3) exist indexes 後，找出一組最適的 index set ，增進資料庫效能。
        * SQL syntax :
        
        > CREATE INDEX index_name ON Table(Atribute)
        > 
        > CREATE INDEX index_name ON Table(A1, A2, ..., An)
        > 
        > CREATE UNIQUE INDEX index_name ON Table(A)
        > 
        > DROP INDEX index_name
        

### B+ tree :
* Rules :
    * two keys per nodes
    * all data is stored in the leaf nodes.
    * every leaf is at same level.
    * all leaf nodes have links to other leaf nodes.
