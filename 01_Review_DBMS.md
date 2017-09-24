# Evolution of DBMS：
  * Punched-Card Record
  * 1914 - 1918 WWI
  * 1929 - 1933 Big Depression ( Bank )
  * 1939 - 1945 WWII
  * 1950 magnetic tape
  * 1955 Programmed Record Managers ( Batch Processing )
      * Con：Transaction error 無法即時被偵測 - didn't know the current situation.
  * 1965 - 1980 On-line Network Database 
      * Indexed sequential records 建立索引
      * Data independence 資料獨立性
            * Physical
            * Logical
      * Concurrent Access 一致性
      * Con：Programming interface are too low level.
  * 1970 E.F. Codd Outline the Relational Model
  * 1976 Peter Chen E-R Model

# ACID：
  * Atomicity：
      * happen or none happen 全有全無
      * IDEA : keep a log ( history ) for all actions
  * Consistency
  * Isolation：每一筆 transaction 都是獨立的
  * Durability：耐久性

# 資料庫的核心是解決人類需求
