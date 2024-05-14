---
title: SQL and NoSQL 該怎麼選？
date: 2024-05-06 14:04:20
tags:
    - SQL
    - NoSQL
categories: Database
---

欸欸，你是用 MySQL嗎？還是你覺得應該用 MongoDB？啊 ! 還是應該用...

<!-- more -->

![Top 15 Databases To Use in 2023 For Web Applications -Ankit Sachan](https://i.ibb.co/k1GYHnj/The-Top-15-Databases-For-Web-Apps-696x232.png)

當選擇資料庫技術時，確實會遇到多種問題和疑慮，這時候就不太適合獨自思考，而是應該與同事、主管以及 stackholders 一起討論，共同尋找最佳解決方案。


以下是簡單了解基本特性，以及可以思考的面向：

### SQL Database: a relational database (RDBS)

- Structured Query Language
- 以 `row 和 column` 方式儲存。每行代表一條記錄，每列代其中一屬性
- 透過外鍵 (Foreign-key) 來強制執行表格之間的關係
- 使用結構化查詢語言（SQL）來查詢和操作數據，包括 SELECT、INSERT、UPDATE、DELETE 等等
- 使用 JOIN 可以處理複雜的查詢
- ACID 特性：原子性（Atomicity）、一致性（Consistency）、隔離性（Isolation）、持久性（Durability

- 較熱門的 SQL databases :
    - MySQL (開源, GPL)
    - PostgreSQL (開源, PostgreSQL)
    - Microsoft SQL Server (商用, 免費版 Express)
    - Oracle (商用, 免費版 Oracle XE)
    - MariaDB (開源, LGPL, 為 MySQL 的分支)

### NoSQL Database

- Not Only SQL
- 為 `Key, Value` 的方式存取，Key 為一個字串，Value 則可以是任意型別（整數、字元、陣列、集合)
- 不需要嚴格要求數據結構，可以很靈活地儲存各種 data type and format
- 未支援傳統資料庫 ACID 的特性，而是遵守 BASE 模型特性: 基本上可用 (Basically Availible)、軟狀態 (Soft State)、最終一致 (Eventually Consistent)

- 多種類型的 NoSQL
  - Key-Value Store
    - 頻繁讀寫的簡單資料模型，內容適合暫時存放的資料
    - [Redis](https://redis.io/) (開源, BSD; 企業版)
  - Document Store: 
    - 以「Document」這個概念，使用的編碼包括 XML 、 YAML 、 JSON 、 BSON (Binary JSON) 等，而內容沒有標準的模式
    - [MongoDB](https://www.mongodb.com/) (開源, AGPL; 企業版)
  - Graph Store
    - 紀錄每個節點與線之間的關係，專門處理高度相互關聯的關係資料，適合用於社交網路，也適合推薦系統、路經尋找等問題
    - [Neo4J](https://neo4j.com/) (開源, AGPL; 企業版)
  - Wide Column Store
    - 可以單獨新增修改 Column 到每一個 Row
    - [Cassandra](https://cassandra.apache.org/_/index.html) (開源, Apache; 企業版)


### 有優勢也有劣勢

簡單來說，
`SQL` 使用結構化查詢語言，非常適合複雜的數據處理任務。學習容易，適合初學者。SQL數據庫在水平擴展上存在困難，垂直擴展成本較高。較適合結構化數據，若數據經常變動或非結構化，管理起來較為困難。

`NoSQL` 較能夠輕鬆實現水平擴展，支持快速更新或查詢大量數據。易於管理複雜的數據結構。支持多種非結構化數據，如音視頻記錄和自然語言文本。如需要 ACID 特性可能就不適合。

### 思考的關鍵因素

- Database Scalability：業務成長帶來的數據量增加
- Complexity of Data Structure：是否具有多變的資料結構
- Query Performance and Optimization：主要操作是大量讀寫還是複雜的查詢
- Development and Maintenance Costs：不同的 DB 技術在開發和維護的成本
- Tech Stack and Team Expertise：開發團隊對哪種 DB 技術更熟悉
- Community Support：可以幫助解決開發過程中遇到的問題


<hr>

Reference:
- [SQL vs NoSQL: 5 Main Differences](https://www.astera.com/knowledge-center/sql-vs-nosql/)
- [When to Use NoSQL vs SQL: The Ultimate Guide for Choosing a Database](https://www.scalablepath.com/back-end/sql-vs-nosql)
- [Top 15 Databases To Use in 2023 For Web Applications](https://www.mobulous.com/blog/top-15-databases-to-use-in-2023-for-web-applications/)
