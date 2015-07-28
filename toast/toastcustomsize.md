# Toast 客製化介面

```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Context context = this;
        String text = "顯示Toast訊息";
        int duration = Toast.LENGTH_SHORT;

        Toast toast = new Toast(context);
        toast.setDuration(duration);
        toast.setText(text); // java.lang.RuntimeException !!
        toast.show();
    }
}
```

* 直接 new 出來的 toast ，預設是沒有介面的。
* 因為沒有介面，執行 setText() 方法時會找到不到可以修改的地方，導致程式拋出例外。

## Toast 顯示文字

```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Context context = this;
        String text = "顯示Toast訊息";
        int duration = Toast.LENGTH_SHORT;

        TextView textView = new TextView(context);
        textView.setText(text);

        Toast toast = new Toast(context);
        toast.setDuration(duration);
        toast.setView(textView);
        toast.show();
    }
}
```

* 新增一個 TextView 元件，並設定文字。
* 使用 toast 物件的 setView() 方法，將元件放到介面中。

## Toast 顯示圖片

```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Context context = this;
        int duration = Toast.LENGTH_SHORT;

        ImageView imageView = new ImageView(context);
        imageView.setBackgroundResource(R.drawable.ic_launcher);

        Toast toast = new Toast(context);
        toast.setDuration(duration);
        toast.setView(imageView);
        toast.show();
    }
}
```

* 新增一個 ImageView 元件，並設定圖片。
* 使用 toast 物件的 setView() 方法，將元件放到介面中。
* 最後可見一個 Toast 顯示並內含圖片。

