# 新增資料

AndroidManifest.xml
```xml
<uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
<uses-permission android:name="com.android.browser.permission.WRITE_HISTORY_BOOKMARKS" />
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 欄位 / 值
        ContentValues valueGroup = new ContentValues();
        valueGroup.put("title", "新增資料");
        valueGroup.put("url", "https://www.google.com.tw/");

        // 新增後回傳一個 Uri，文件說是新資料列的 URL，不太瞭解是什麼意思，新增失敗時拿到 NULL。
        Uri uri = Uri.parse("content://browser/bookmarks");
        Uri result = getContentResolver().insert(uri, valueGroup);

        TextView v = new TextView(this);
        v.setText((result != null) ? "Success" : "Fail");
        setContentView(v);
    }
}
```