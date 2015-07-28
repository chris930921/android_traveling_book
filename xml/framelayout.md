# FrameLayout

```xml
<FrameLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#ffff00" >

    <Button
        android:layout_width="300dip"
        android:layout_height="300dip"
        android:background="#0000ff" />

    <Button
        android:layout_width="200dip"
        android:layout_height="200dip"
        android:background="#00ff00" />

    <Button
        android:layout_width="100dip"
        android:layout_height="100dip"
        android:background="#ff0000" />

</FrameLayout>
```

* 父框架背景是黃色
* 父框架第一個子元件是藍色，大小300x300
* 父框架第二個子元件是綠色，大小200x200
* 父框架第三個子元件是鴻色，大小100x100
* 上一層的子元件或子框架，會被下一層的子元件或子框架蓋住。
* 預設將元件放在左上角。

