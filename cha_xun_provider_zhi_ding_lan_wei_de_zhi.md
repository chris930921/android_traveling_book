# 查詢 Provider 指定欄位的值

AndroidManifest.xml
```xml
<uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 以瀏覽器書簽為例
        Uri uri = Uri.parse("content://browser/bookmarks");

        // 指定名稱為 title、url 的欄位，讀取索引分別是 0、1
        String[] fields = {"title", "url"};

        //查詢
        Cursor cursor = getContentResolver().query(uri, fields, null, null, null);

        String text = "";
        // 移動讀取指標直到結束，回傳 false 跳出迴圈
        while (cursor.moveToNext()) {
            // 讀取 title
            text += cursor.getString(0) + "\n";
            // 讀取 url
            text += cursor.getString(1) + "\n";
        }

        // 設定並顯示畫面
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```