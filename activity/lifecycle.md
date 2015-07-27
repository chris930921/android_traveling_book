# LifeCycle

#### onCreate
* 對Activity類別的屬性作初始化
* 此階段還不會顯示畫面

#### onRestart


#### onStart
* Activiy 可見

#### onResumed
* Activity 可見。
* 適合執行動畫的階段。
* 重新取回硬體資源。

#### onPaused
* 開啟 Dialog 雖會讓Activity畫面加暗並顯示視窗，但不會導致Activity進入此狀態。
* Activity 可見。
* 不執行程式碼。
* 釋放硬體資源。

#### onStopped
* Activity 不可見
* Activity 不再前台

#### onDestory
* Activity 關閉
