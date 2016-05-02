# 有條件的進行查詢 - 前後部份比對

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Uri uri = Uri.parse("content://browser/bookmarks");
        String[] fields = {"title"};

        // LIKE 部份比對
        String selectionClause = "title LIKE ?";

        // 指定 title 欄位內容含有 "Android" 字串的資料列
        String[] selectionArg = {"%Android%"};

        Cursor cursor = getContentResolver().query(uri, fields, selectionClause, selectionArg, null);
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