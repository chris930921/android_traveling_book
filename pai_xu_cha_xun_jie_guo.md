# 排序查詢結果

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

        Uri uri = Uri.parse("content://browser/bookmarks");
        String[] fields = {"_id"};

        String selectionClause = "_id < ?";
        String[] selectionArg = {"20"};

        // 依照 _id 欄位由大到小排序
        String sortOrder = "_id DESC";
        // 依照 _id 欄位由小到大排序
        // String sortOrder = "_id AES";

        Cursor cursor = getContentResolver().query(uri, fields, selectionClause, selectionArg, sortOrder);
        String text = "";
        while (cursor.moveToNext()) {
            text += cursor.getString(0) + "\n";
        }

        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```
