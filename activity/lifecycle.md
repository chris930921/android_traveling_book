# LifeCycle

#### OnCreate
* 對Activity類別的屬性作初始化
* 此階段還不會顯示畫面

#### OnStart
* Activiy 可見

#### OnResumed
* Activity 可見。
* 適合執行動畫的階段。
* 重新取回硬體資源。

#### OnPaused
* 開啟 Dialog 雖會讓Activity畫面加暗並顯示視窗，但不會導致Activity進入此狀態。
* Activity 可見。
* 不執行程式碼。
* 釋放硬體資源。

#### OnStopped
* Activity 不可見
* Activity 不再前台

#### OnDestory
* Activity 關閉
