# 有條件的進行查詢 - 數值比對

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Uri uri = Uri.parse("content://browser/bookmarks");
        String[] fields = {"_id"};

        // 數值比對
        String selectionClause = "_id < ?";
        String[] selectionArg = {"10"};

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