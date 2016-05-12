# 查詢條件 - 統計資料

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
        realm.beginTransaction();
        for (int i = 0; i < 10; i++) {
            TableName table = realm.createObject(TableName.class);
            table.setFieldName(i);
        }
        realm.commitTransaction();

        // 建立查詢資料的 query 物件，尋找 fieldName 欄位大於等於 6 的資料項。
        RealmQuery<TableName> query = realm.where(TableName.class).lessThanOrEqualTo("fieldName", 6);
        TableName result = query.findFirst();
        String text = result.getFieldName() + "";

        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```