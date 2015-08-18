# notifyDataSetChanged 更新內容

```java
public class MainActivity extends Activity {
    private String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 設定 ListView 內容。
        final ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this, android.R.layout.simple_list_item_1, strGroup);
        ListView list = new ListView(this);
        list.setAdapter(adapter);

        //設定按鈕，按下後更新 ListView 內容。
        Button button = new Button(this);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                // 修改陣列內容
                strGroup[0] = "更改字串1";
                strGroup[1] = "更改字串2";

                // 通知資料被變動，更新 ListView 顯示內容。
                adapter.notifyDataSetChanged();

            }
        });

        // 排版框架
        LinearLayout container = new LinearLayout(this);
        container.setOrientation(LinearLayout.VERTICAL);
        container.addView(button);
        container.addView(list);

        //設定畫面
        setContentView(container);
    }
}
```
