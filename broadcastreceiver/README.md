# BroadcastReceiver

* 註冊接收器 -> 發送廣播 -> 收到廣播執行動作。

* 透過 ACTION 內容來過濾廣播，決定是否接收。

* 分成靜態註冊和動態註冊兩種。

* 靜態註冊 : 在 AndroidManifest.xml 中註冊。

* 動態註冊 : 在程式中用 registerReceiver() 方法註冊。

* Activity 與 Service 溝通的媒介。

* 也可以接收其他系統事件，如開機事件、簡訊事件等。
