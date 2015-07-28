# EditText

```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```
* 文字輸入框
* 可以限制輸入的文字類型。
* 可以限制輸入的長度。
* 可以都多行輸入。


## 字體大小
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textSize="50px"/>
```
* android:textSize

## 字體顏色
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textColor="#0000FF"/>
```
* android:textColor

## 提示訊息
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:hint="email"/>
```
* android:hint
* 顯示在背景的較淡色文字
* 常用來提示使用者要輸入什麼資訊
* 輸入框有游標時會消失


## 關閉輸入功能
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:editable="false"/>
```
* android:editable
* true *開啟*
* false *關閉*
* 預設是 true 開啟

## 密碼輸入模式
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:password="true"/>
```
* android:password
* 輸入文字後會變成星號 * 掩蓋密碼。
* true *打開模式*
* false *關閉模式*
* 預設是 false 關閉

## 限制輸入數字
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:inputType="number"/>
```
* android:inputType
* 限制使用者只能輸入何種類型的文字。
* number *只能輸入正整數*
* numberSigned *只能輸入正負整數*
* numberDecimal *可以輸入含小數點的數字*
* textMultiLine *可以輸入多行*

## 直接限制輸入
```xml
<EditText
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:digits="123ABCㄛ是喔"/>
```
* android:digits
* 直接限制使用者只能輸入哪些字元。

