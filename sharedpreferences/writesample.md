# 寫入資料範例

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String fileName = "save_file";
        SharedPreferences sharedPreferences = getSharedPreferences(fileName, Context.MODE_MULTI_PROCESS);
        //取得SharedPreferences的編輯器。
        SharedPreferences.Editor editor = sharedPreferences.edit();
        //在KeyNameOne欄位放入字串Something。
        editor.putString("KeyNameOne", "Something");
        //儲存修改。
        editor.commit();

        //利用KeyNameOne名稱取得字串。
        String valueOne = sharedPreferences.getString("KeyNameOne", "Nothing");
        TextView v = new TextView(this);
        v.setText(valueOne);
        //設定介面
        setContentView(v);
    }
}

```
