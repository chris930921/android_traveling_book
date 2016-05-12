# 查詢條件 - 完全比對

TableName.java
```java
public class TableName extends RealmObject {
    private int fieldName;

    public void setFieldName(int fieldName) {
        this.fieldName = fieldName;
    }

    public int getFieldName() {
        return fieldName;
    }
}
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    @RealmModule(classes = {TableName.class})
    public static class Module {
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        RealmConfiguration config = new RealmConfiguration.Builder(this)
                .name("database_name.realm")
                .setModules(new Module())
                .build();
        Realm realm = Realm.getInstance(config);

        // 開始資料庫交易，新增資料。
        realm.beginTransaction();
        for (int i = 0; i < 10; i++) {
            TableName table = realm.createObject(TableName.class);
            table.setFieldName(i);
        }
        realm.commitTransaction();

        // 建立查詢資料的 query 物件，尋找 fieldName 欄位等於 6 的資料項。
        RealmQuery<TableName> query = realm.where(TableName.class).equalTo("fieldName", 6);

        // 取得查詢後的資料，這裡簡化過程只取出第 1 項。
        TableName result = query.findFirst();
        String text = result.getFieldName() + "";

        // 顯示結果
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```