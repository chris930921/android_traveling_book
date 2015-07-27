### LinearLayout 基本屬性要求

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    android:orientation="vertical">
 </LinearLayout>
```

* android:orientation 決定是水平排列或是垂直排列
* vertical 垂直排列
* horizontal 水平排列

### 垂直排列 Button

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button 1" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button 2" />

</LinearLayout>
```
### 水平排列 Button

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button 1" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button 2" />

</LinearLayout>
```
