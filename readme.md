# Database migration tools dbmate

此專案是使用 docker compose 來開啟 MySql 容器並進入容器使用 dbmate 來建立資料庫。

在軟體工程中，對於資料庫的版本控制，即是指遷移 ( Migration )，而這之中有可分為兩個不同的遷移機制：

+ 資料庫遷移 ( Database Migration )
> 主要版本管理資料庫欄位的改變與版本

+ 資料遷移 ( Data Migration )
> 主要探討資料庫間移轉資料的機制

DBmate 是用於資料庫遷移，並非專門用於資料遷移機制，這類工具有助於管理資料庫的變更，但對於實裝於產品環境中的資料庫應注意在欄位變更的機制中是否會導致資料遺失。

## 指令

+ 啟動虛擬環境
```
dockerw start
```

+ 關閉虛擬環境
```
dockerw down
```

+ 進入容器
```
dockerw into
```

+ 進入容器
```
dockerw up
```
> 依據專案相依設定合併 migrations 目標，並執行 ```dbmate up```

+ 檢查遷移狀態
```
dockerw status
```

## DBmate 操作

+ DBmate 執行資料遷移
```
dbmate up
```
> 此命令會根據當前目錄下 ```db/migrations``` 的 sql 檔進行資料庫建立，建立順序是依據檔名前方的 timestamp 來排序
>
> 若已經建立後在增加 .sql 檔案，則會依據當前更新的時間點在往後更新

+ DBmate 執行資料庫備份
```
dbmate dump
```
> 此命令是執行 ```mysqldump```，並將備份檔案匯出至當前目錄下的 ```db``` 中
>
> 倘若將 dbmate 與 mysql 分為兩個容器將無法運作
>
> 此工具執行的指令受限，倘若需詳細設定備份機制，應使用 ```mysqldump``` 來構成需要的命令

## 參考

#### DBmate document

+ [Docker hub: MySQL](https://hub.docker.com/_/mysql)
+ [Docker hub: DBmate](https://hub.docker.com/r/amacneil/dbmate)
    - [DBmate github](https://github.com/amacneil/dbmate)
+ [W3Schools SQL](https://www.w3schools.com/sql/default.asp)
    - [SQL Create Table](https://www.w3schools.com/sql/sql_create_table.asp)
    - [SQL Alter Table](https://www.w3schools.com/sql/sql_alter.asp)
    - [SQL Foreign key](https://www.w3schools.com/sql/sql_foreignkey.asp)
+ [Mysqldump — A Database Backup Program](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)

#### Migration

+ [Schema migration](https://en.wikipedia.org/wiki/Schema_migration)
    - [Why database migrations?](https://flywaydb.org/documentation/getstarted/why)
    - [What Is Database Migration?](https://dzone.com/articles/what-is-database-migration)
+ [使用 DMS 在線上將 MySQL 移轉至適用於 MySQL 的 Azure 資料庫](https://docs.microsoft.com/zh-tw/azure/dms/tutorial-mysql-azure-mysql-online)
    - [Azure Database Migration Guide](https://datamigration.microsoft.com/)
+ [MBA 智庫：資料遷移 ( Data Migration )](https://wiki.mbalib.com/zh-tw/%E6%95%B0%E6%8D%AE%E8%BF%81%E7%A7%BB)
+ [How To Migrate a MySQL Database Between Two Servers](https://www.digitalocean.com/community/tutorials/how-to-migrate-a-mysql-database-between-two-servers)
