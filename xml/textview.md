# TextView

## 顯示文字

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World"/>
```
* android:text

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/hello_world"/>
```
* 可以用 @string/ 前輟，指定顯示 string.xml 的字串。

## 字體大小

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World"
    android:textColor="#0000FF"
    android:textSize="50px" />
```

* android:textSize
* 單位px

## 字體顏色

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World"
    android:textColor="#0000FF"/>
```
* android:textColor

## 字體型式

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World"
    android:textStyle="bold"/>
```
* android:textStyle
* normal *一般字體*
* bold *粗體*
* normal|italic *一般字體+斜體*
* bold|italic *粗體+斜體*

## 是否換行
```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="wow ,very logic ,wow ,many science ,wow ,so reserch ,wow ,very smart ,wow "
    android:singleLine="true"/>
```
* android:singleLine
* true *文字太長不換行*
* false *文字太長換行*

## 文字過長處理模式
```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="wow ,very logic ,wow ,many science ,wow ,so reserch ,wow ,very smart ,wow "
    android:singleLine="true"
    android:ellipsize="end"/>
```
* android:ellipsize
* none *不處理*
* start *文字開始處省略成...。*
* middle *文字中間處省略成...。*
* end *文字結尾處省略成...。*
* marquee *以滾動方式顯示。*
