# RelativeLayout 相對於父框架

* true 是對齊。
* false 是不對齊。

## 對齊父框架的左下方

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentLeft="true"
        android:layout_alignParentBottom="true"
        android:text="Button 1" />

</RelativeLayout>
```
* android:layout_alignParentLeft
* 對齊父框架左邊
* android:layout_alignParentBottom
* 對齊父框架下方

## 對齊父框架的右上方

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:layout_alignParentTop="true"
        android:text="Button 1" />

</RelativeLayout>
```
* android:layout_alignParentRight
* 對齊父框架右邊
* android:layout_alignParentTop
* 對齊父框架上方

## 對齊父框架的水平中心

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="Button 1" />

</RelativeLayout>
```
* android:layout_centerHorizontal
* 置於父框架水平中心

## 對齊父框架的垂直中心

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerVertical="true"
        android:text="Button 1" />

</RelativeLayout>
```

* android:layout_centerVertical
* 置於父框架水平中心


## 對齊父框架的正中心

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Button 1" />

</RelativeLayout>
```

* android:layout_centerInParent
* 置於父框架水平、垂直中心
