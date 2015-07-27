
## 設定大小

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"
    android:layout_height="match_parent">
</RelativeLayout>
```
#### 數值部分可以有以下選擇

* match_parent 填滿父框架
* wrap_content 自適應內容
* 100 dip 單位
* 100 dp 單位
* 100 px 單位

## 設定背景顏色

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    android:background="#ffff00">
</RelativeLayout>
```

* 顏色使用 16 進位表示。
* 開頭要帶 # 字號。
* 由 6 個 16 進制數字組成。
* 每 2 數字分成 1 組。
* 這 3 組各代表紅綠藍( RGB )的分配。

```xml
#ff0000 代表紅色
#00ff00 代表綠色
#0000ff 代表藍色
#ffff00 代表黃色，由紅色和綠色混合產生。
```

## 設定名稱
```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#ffff00"

    android:id="@+id/max_layout">
</RelativeLayout>
```

* 名稱前面要加上前輟 @+id/，IDE才會知道要把名稱放進R.java中。
* 可以用在程式中，藉由名稱取得元件的控制權。
* 可以用再排版中，讓其他元件或框架藉由名稱，來做對齊。

## 範例
```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#00ff00">

    <RelativeLayout
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:background="#ffff00">
    </RelativeLayout>

</RelativeLayout>
```

* 在最大框架中，加入一個子框架。
* 設定子框架長寬為 100 dp。
* 可以見到整體父框架背景為綠色。
* 可以見到左上角有一個黃色正方形的子框架。
