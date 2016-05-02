# 列出 Provider 所有的欄位


```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
        // 以瀏覽器書籤為例
        Uri uri = Uri.parse("content://browser/bookmarks");
        
        // 作 SELECT * 查詢
        Cursor cursor = getContentResolver().query(uri, null, null, null, null);
        
        // 每欄名稱印出後換行
        String text = "";
        for (int i = 0; i < cursor.getColumnCount(); i++) {
            text += cursor.getColumnName(i) + "\n";
        }
        
        // 顯示再畫面上
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```