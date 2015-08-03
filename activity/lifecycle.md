# LifeCycle

[Activity LifeCycle](http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle)

#### onCreate
* Activity 被建立或手機翻轉。
* 設定畫面。
* 對屬性作初始化。

#### onRestart
* 從 onStop 狀態回到 onStart 狀態。
* 重新開啟 Activity 時觸發。

#### onStart
* Activity 從不可見變為可見。
* Activity 從後台 ( Background ) 進入到前台 ( Foreground ) 。
* 不可見情況: 完全被另一個Activity蓋住。
* 不可見情況: 螢幕顯示進入休眠。
* 不可見情況: 退出 Activty。

#### onResumed
* Activity 從部分可見變為完全可見。
* 適合執行動畫的階段。
* 因為葉面進入啟動狀態，應該重新取回硬體資源。

#### onPaused
* Activity 從完全見變成部分可見。
* 部分可見情況: 被一個透明的 Actvitiy 蓋住。
* 開啟 Dialog 雖會讓 Activity 畫面加暗並顯示視窗，但不會導致Activity進入此狀態。
* 暫停執行這個 Activity 程式碼。
* 因為頁面進入暫停狀態，應該釋放硬體資源。

#### onStopped
* Activity 從可見變成不可見。
* Activity 從前台 ( Foreground ) 進入到後台 ( Background ) 。
* 不會和使用者有交流。

#### onDestory
* Activity 執行 finish() 方法後關閉。
* 手機螢幕翻轉，介面重繪。


## 流程
#### entire lifetime
* 完整生命時間
* 從 onCreate -> onStart -> onResumed -> onPaused -> onStopped -> onDestory

#### visible lifetime
* 可見生命時間
* 從 onStart -> onResumed -> onPaused -> onStopped
* 可能會執行多次。
* 適合維護與介面顯示有關的 BroadcastReceiver。

#### foreground lifetime
* 前景生命時間
* 從 onResumed -> onPaused
* 會在各種情況繁執的執行，裝置的睡眠、其他 Activity 的結果回傳，這裡的程式應盡可能減少。
