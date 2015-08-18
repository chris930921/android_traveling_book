# OnItemLongClickListener 長按事件


#### 長按後 Active 狀態保持。
```java
public class MainActivity extends Activity {
    public Activity activity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;

        final String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        v.setOnItemLongClickListener(new AdapterView.OnItemLongClickListener() {
            @Override
            public boolean onItemLongClick(AdapterView<?> adapterView, View view, int index, long l) {
                // 利用索引值取得點擊的項目內容。
                String text = strGroup[index];
                // 整理要顯示的文字。
                String result = "索引值: " + index + "\n" + "內容: " + text;
                // 顯示。
                Toast.makeText(activity, result, Toast.LENGTH_SHORT).show();
                // 回傳 false，長按後該項目被按下的狀態會保持。
                return false;
            }
        });
        setContentView(v);
    }
}
```

#### 長按後 Active 狀態消失。

```java
public class MainActivity extends Activity {
    public Activity activity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;

        final String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        v.setOnItemLongClickListener(new AdapterView.OnItemLongClickListener() {
            @Override
            public boolean onItemLongClick(AdapterView<?> adapterView, View view, int index, long l) {
                String text = strGroup[index];
                String result = "索引值: " + index + "\n" + "內容: " + text;。
                Toast.makeText(activity, result, Toast.LENGTH_SHORT).show();
                // 回傳 true，長按後該項目被按下的狀態會消失。
                return true;
            }
        });
        setContentView(v);
    }
}
```
