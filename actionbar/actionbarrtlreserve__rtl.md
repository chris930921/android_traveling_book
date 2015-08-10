# ActionBar 非正規的 RTL 反轉

#### AndroidManifest.xml 的 Application 標籤加入。
```xml

<application
    ...
    android:supportsRtl="true">
</application>

```

#### MainAcivity 範例
```java
public class MainActivity extends Activity {
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 將 ActionBar 元件拉出來
        Window window = getWindow();
        View v = window.getDecorView();
        int resId = getResources().getIdentifier("action_bar_container", "id", "android");
        View actionBar = v.findViewById(resId);

        //用 setLayoutDirection 做介面反轉
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.JELLY_BEAN_MR1) {
            actionBar.setLayoutDirection(View.LAYOUT_DIRECTION_RTL);
        }

        //顯示左邊的按鈕當作範例
        ActionBar bar = getActionBar();
        bar.setDisplayHomeAsUpEnabled(true);
    }
}
```

* 在多國語言版本上也許會有副作用。
