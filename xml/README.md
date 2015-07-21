# XML 排版初探

做 Android 介面排版時，可把以下原則:

#### Android 介面中只分兩種類型的物件，這兩種物件都可統稱作View

* 排版框架( Container )

* 功能元件( Component )

#### 名稱定義

* XML中第一層框架，稱作最大框架。

* 框架內又可以放其他的框架或元件，稱作子框架或子元件。

* 包住子框架或子元件的框架，稱作父框架。

#### 基本屬性，無論框架或元件應該擁有以下屬性

* 寬度 android:layout_width

* 高度 android:layout_height

* 名稱 android:id

#### 每次編輯結束應按以下快捷鍵，排版有助美觀與理解，儲存有助於消除錯誤。

Eclipse ( 快速排版 + 儲存 )

* ctrl + shift + F

* ctrl + S

Android Studio ( 快速排版 + 儲存 )

* ctrl + alt + L

* ctrl + S

#### 新手常犯的錯誤

* 將 android 打為 andorid，導致提示視窗無法出現。

* 將 EditText 打為 EditView，導致排版頁面無法預覽。

* 編輯後沒有儲存讓錯誤提示消除，以為 XML 中仍存在錯誤。
