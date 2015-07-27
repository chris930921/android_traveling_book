# RelativeLayout 相對於子元件或子框架

## 基礎框架

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:text="Button 2" />

</RelativeLayout>
```

* android:id="@+id/..."
* 被對齊的子元件或子框架應該設定ID。
* 設定ID的目的是為了讓其他的子元件或子框架有目標能對齊。
* 其他子元件或子框架對設定目標時，ID不用有+號。
* 中心按鈕較大(200x20)，對齊按鈕較小(100x100)，是為了加強上下左右對齊的效果。

## 被對齊元件的上方，且左邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_above="@id/center_button"
        android:layout_alignLeft="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的上方，且右邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_above="@id/center_button"
        android:layout_alignRight="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的下方，且左邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_below="@id/center_button"
        android:layout_alignLeft="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的下方，且右邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_below="@id/center_button"
        android:layout_alignRight="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的左方，且上邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toLeftOf="@id/center_button"
        android:layout_alignTop="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的左方，且下邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toLeftOf="@id/center_button"
        android:layout_alignBottom="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的右方，且上邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toRightOf="@id/center_button"
        android:layout_alignTop="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

## 被對齊元件的右方，且下邊對齊。

```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/center_button"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:text="Button 1" />

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toRightOf="@id/center_button"
        android:layout_alignBottom="@id/center_button"
        android:text="Button 2" />

</RelativeLayout>
```

