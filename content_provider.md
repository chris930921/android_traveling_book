# Content Provider

* 應用程式間用來交換數據的一種管道
* 當作在使用 Sql 資料庫就可以了，很相似
* 可查詢、新增、刪除、更新

```java
//查詢方法
public abstract Cursor query (Uri uri, String[] projection, String selection, String[] selectionArgs, String sortOrder)
```

* uri，類似資料表名稱
* projection，類似資料表欄位名稱
* selection，類似 WHERE 條件描述，以 ？ 當作輸入做參數化查詢
* selectionArgs，類似參數化查詢，提供每個 ? 數值輸入
* sortOrder，類似排序功能