# Toast 使用方式

```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Context context = this;
        String text = "顯示Toast訊息";
        int duration = Toast.LENGTH_SHORT;

        Toast.makeText( context , text , duration).show();
    }
}

```

* 第一個參數傳入 Activity 本身
* 第二個參數傳入要顯示的文字訊息。
* 第三個參數傳入顯示時間的長度。


* Activity 之所以能夠放入 Context 型態的的參考，是因為他們有繼承關係。
* 顯示時間長度只有兩種可以選擇。
* Toast.LENGTH_SHORT 短時間顯示。
* Toast.LENGTH_LONG 長時間顯示。


## 細節解析: 取得 Toast 物件並設定。

```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Context context = this;
        String text = "顯示Toast訊息";
        int duration = Toast.LENGTH_SHORT;

        Toast toast = Toast.makeText( context , text , duration);
        toast.setText("改變Toast訊息");
        toast.show();
    }
}

```
* Toast.makeText() 靜態方法會回傳一個 Toast 型態的物件。
* 宣告一個 Toast 型態的參考將物件儲存起來。
* 運用 Toast 物件的 setText() 方法改變內容。
* 運用 Toast 物件的 show() 方法顯示內容。

