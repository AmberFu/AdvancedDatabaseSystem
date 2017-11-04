## Multidimensional and Multimedia Databases

Related Videos

### [On-Line Analycital Processing (OLAP) - Introduction](https://www.youtube.com/watch?v=jcl0unn73RY&feature=youtu.be) ( by Prof. Jennifer Widom )

##### Two broad types of database activity:

###### OLTP - On-Line Transaction Processing:

* Short transactions
* Simple querise
* Touch small portions of data
* Frequent updates

###### OLAP - On-Line Analytical Processing:

* Long transactions
* Complex queries
* Touch large portions of data
* Infrequent updates

> 以上兩種雖然看似兩個極端，但在 Database system 原以 OLTP 為主，特殊技術致力於 OLAP ，
>
> 因此資料庫中兩中方式都可行，端看需求來調整使用類型。
>

###### 其他專有名詞 ( treminology )

* Data warehousing

        Bring data from operational 營運的 (OLTP) sources into a single "warehouse" for OLAP analysis.

* Decision Support System (DSS)

        infrastructurd for data analysis 

* Star schema

        ''
