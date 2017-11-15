# Relational Model：

* Data Model - a language to description data
* 名詞對照：
    * Relation = Table
    * Attribute / Field = Column
    * Record / Tuple = Row
* Constraint Type：關聯模型的限制
    1. Domain constraints - for value of each attribute
        - 將 attribute 設定好後，DBMS 會進行檢查，若欄位設定是年齡，則輸入值只能是正整數！（若都設定成 str ，則只檢查長度，反而要另外寫程式進行 input 檢查）
    2. Key constraints - for Primary key 
        - All tuples in a relation must be distinct !
    3. Entity integrity constraints 實體完整性限制 - for Primary key
        - No Primary key value can be null !
    4. Referential Integrity constraints 參考完整性限制 - for Primary key and Foreign key
        - If a foreign key (FK) is refers to another relation's primary key (PK), then FK's values MUST EXIST in PK's value or null ! ( 外鍵的值必須存在在主鍵的鍵值中，或是 null 值。)
        - A foreign key can refer to its own relation.
        - Circular referential integrity constraints are allowed.
    Normalization of relations 資料正規化
        Normalization - to process of decomposing（分解） unsatisfactory（令人不滿的）"bad" relation by breaking up their attributes into smaller relations.

* Summary of five Normal Forms 五種正規化：
    1. 第一正規化 ( 1 NF )：
        - attribute value is "atomic value"
        - 單一欄位內只能有一筆資料
        - 確認資料表中的主鍵
        - 確認表單內所有的欄位，都要與主鍵有關係（具相依性）
    2. 第二正規化 ( 2 NF )：
        - non-key field must totally dependent on primary key
        - 消除部分功能相依（Partial Functional Dependency）：Non-key 與 Primary-key 
    3. 第三正規化 ( 3 NF )：
        - It must independent between non-key field ( just dependent on primary key or candidate key )
        - 消除資料表中的遞移相依（Transitive Functional Dependency）
            - 遞移相依是指有些欄位資料，在 Table 中，可以由某個 non-primary key 的欄位決定
            
            ex:
            
               | Class ID | Class Name | Teacher ID | Teacher Name |
               | -------- | ---------- | ---------- | ------------ |
               | 001 | ADB | T01 | AAA |
               | 002 | DataMining | T01 | AAA |
               | 003 | Python | T02 | BBB |
               
               當 Primary Key 為 Class ID，
                  Class ID --> Class Name / Teacher ID / Teacher Name
                  Teacher ID --> Teacher Name (為遞移相依性，Non-key 與 Non-key 之間）
              
    4. 第四正規化 ( 4 NF )：
        - A record type should not contain two or more independent multi-values facts about an entity.
        - 解決多值相依問題
    5. 第五正規化 ( 5 NF )： *不太懂...
        - 解決合併相依問題 (Join Dependency) - 合併相依是指當關聯表分割成3個或更多關聯表後, 一定能夠透過多次合併運算恢復成原來的關聯表。

* FUNCTIONAL DEPEDENCIES 功能相依：

描述屬性之間的關係就是「功能相依」，當 A 資料值可唯一決定 B 的資料值時，則 B 功能相依於 A 。( A --> B )
