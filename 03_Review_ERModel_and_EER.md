# E-R Model：
> 一般實體關係：|實體| ----- <關係> ----- |實體| 
>
> 弱實體關係：|實體| ------ <<關係>> ----- ||實體||

* 實體關係模型由：
    * Entity 實體（方形）：
        * 名詞：
            * Entity type name 即 Table name
            * Entity 的 Attribute 即 column name
            * Entity 的 Attribute value 即 欄位的值
            * Entity set：instance 的集合
            * Entity class：described by Attribute
            * Entity Instance 實例（ a tuple or a record )
        * Entity Type：
            * Weak Entity（弱實體）：須依靠其他實體才能存在。（雙實線方框）
            * Strong Entity ( regular entity ，一般實體)
    * Relationship 關係 （菱形）<R>
        * 圖示：
            * 弱關係以 雙實線 菱形 表示 <<R>>
            * 一般關係以 單實線 菱形 表示 <R>
        * High-Level Entity：（講義 p.19）？！
        * N-ary relationship：
            * Unary relationship (Degree 1)：
                * 又稱 Recursive Relationship（遞迴關係）
                * 只與自己產生關係 

            * Binary relationship (Degree 2)：
                * |Entity A|--<R>--|Entity B|
                * <Relationship> 只與兩個 Entity 產生關係 
            * Ternary relationship (Degree 3)：
                * <Relationship> 與三個以上的 Entity 產生關係
                * Type：
                    * |Entity|---M----<R>----N----|Entity|
                    * 1 : 1 （一對一）Binary relationship
                    * 1 : N （一對多）Binary relationship
                    * N : 1 （多對一）Binary relationship
                    * M : N （多對多）Binary relationship
        * Cardinality（參與數的限制，基數） 
            * |Entity|--{min,max}--<R>--{min,max}--|Entity|
            
    * Participation 參與（實體與關係的連接線）
        * 圖示：
            * 完全參與（ Total Participation ）：以 雙橫線 表示 (===)
                * 1 === 1 （ 一對一 完全參與 ）
                * M === N （ 多對多 完全參與 ）
                * 1 === N / N === 1 （ 一對多 / 多對一 完全參與 ）
            * 部份參與（ Partial Participation ）：以 單橫線 表示 (---)
                * 1 --- 1 （ 一對一 部份參與 ）
                * M --- N （ 多對多 部份參與 ）
                * 1 --- N / N --- 1 （ 一對多 / 多對一 部份參與 ）
                
    * Attribute 屬性（橢圓）
        * Attribute Type：
            * Key Attribute：
                * 具唯一性
                * 不可重複
                * 不可為 Null
                * regular entity 的 PK 鍵畫實線底線 ( ____ )
                * weak entity 的 PK 鍵畫虛線底線 ( _ _ _ )
            * Atomic attribute（不能再分割的最小屬性）
            * Single value（單值屬性） ：如 性別。
            * Derived attribute（推導屬性）以 虛線 橢圓 表示。（如：年齡 - 可由生日與目前時間推導出來）
            * Composite attribute（複合屬性）：若某個屬性可在細分成多個小屬性，就再細分延伸一層。（如：姓名 - 可以在細分成 姓 & 名）
            * Multi-valued attribute（多值屬性）：當某個屬性有一個以上的值時，以 雙實線 橢圓 表示  
        * ER model 轉換成 relational model：
            * 針對 Strong Entity：
                * Entity 是 table
                * Attribute 化為 column，放入不同 attribute 特性：
                    * Primary Key
                    * Foreign Key
            * 針對 Weak Entity：
                * Entity 是 table
                * Attribute 包含：
                    * 所有 weak entity attribute + 依賴的 strong entity PK 鍵
                    * PK 鍵 包含：
                        * 部份 weak entity attribute + 
                        * 依賴的 strong entity PK 鍵
            * 針對 M:N relationship：
                * |Entity A1|---M---<R>---N---|Entity A1|：打破成 M:1 & 1:N
                * 新增一個多對多關係的關聯表，將 M 與 N 的 PK 組合起來成為此表的 Primary key
            * 針對 1:N / N:1 relationship：
                * N 端的 Table 加入一個 Foreign key 參考到 1端的 Primary key
            * 針對 1:1 relationship：
                * |Entity A|---1---<R>---1---|Entity B|
                * 擇一加入一個 Foreign key：
                    * 若只有一端完全參與，則選擇該端加入 Foreign key
                    * 如果兩端都不是「完全參與」，則選擇其中「基數」較少者加入 Foreign key
                    * 如果兩端都是「完全參與」，可以將兩個 Entity 與 <R> 結合成一個關聯表格。

# Extended ER（ EER，擴充實體關聯模型）：
當某些 Relationship 只關聯到一個 Entity Set（ex: 員工） 中的某些 Entity（ex: IT, sales, marketing...）。
    
* 一個 Super type 可以有多個 Sub type 繼承其屬性：（類似多載觀念）
   * Super type：共通的超類型屬性
   * Sub type：共通的超類型屬性 + 特殊屬性
   * 以 ISA ( is a ) 倒三角形表示特殊化關係
   * 轉化方式：
      * Specialization： Super Type --> 依特殊性區分出 Sub Type
      * Generalization：Sub Type --> 歸納出 Super Type
   * 依照實體在子類型中的隸屬關係，可區分為：
      * disjoint 不相交 （d)  ex: 學生--(d)-- 大學生 / 國中生 ...
      * overlap 重疊 （o）ex: 客戶--(o)-- 租屋者 / 買屋者 ...
