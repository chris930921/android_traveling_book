# SharedPreferences

* Android 中用來儲存資料的功能。
* 會將資料儲存在 APP 的專用空間。
* 只能夠儲存基本型態 ( String、int、float、long、boolean )。
* 採用 Key-Value 的形式儲存、讀取。

## 設定存取模式

* MODE_PRIVATE 不同程序讀取不同資料來源
* MODE_MULTI_PROCESS 多個程序讀取同一個資料來源
* MODE_WORLD_READABLE 其他的 APP 可以讀取自己 APP 的資料來源
* MODE_WORLD_WRITEABLE 其他的 APP 可以讀取、寫入自己 APP 的資料來源
