# 建立資料表並新增、查詢資料

TableName.java
```java
public class TableName extends RealmObject {
    // 其他可作為欄位的基本型態有
    // boolean, byte, short, ìnt, long, float,
    // double, String, Date, byte[]

    // 名稱部份可隨意取名，代表該欄位名稱。
    private int fieldName;

    // 需設定該欄位的 setter 方法
    public void setFieldName(int fieldName) {
        this.fieldName = fieldName;
    }

    // 需設定該欄位的 getter 方法
    public int getFieldName() {
        return fieldName;
    }
}
```

MainActivity.java
```java
public class MainActivity extends Activity {

    // 設定 Module，指定包含哪些資料表。
    @RealmModule(classes = {TableName.class})
    public static class Module {
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 建立 config 物件，設定資料庫名稱和 module。
        RealmConfiguration config = new RealmConfiguration.Builder(this)
                .name("database_name.realm")
                .setModules(new Module())
                // 如上次以建立過相同名稱資料庫，但欄位結構已經改變時，會刪除舊資料庫，不是實務上的必要動作。
                .deleteRealmIfMigrationNeeded()
                .build();
        // 根據設定建立 realm 物件。
        Realm realm = Realm.getInstance(config);

        // 開始資料庫交易。
        realm.beginTransaction();
        // 這裡清空資料表，只是為了保持乾淨讓執行結果正常，不是實務上的必要動作。
        realm.clear(User.class);
        // 建立資料物件，並設定數值。
        for (int i = 0; i < 10; i++) {
            TableName table = realm.createObject(TableName.class);
            table.setFieldName(i);
        }
        // 完成資料庫交易。
        realm.commitTransaction();

        // 建立查詢資料的 query 物件。
        RealmQuery<TableName> query = realm.where(TableName.class);
        // 取出所有的資料，檢查是否有新增成功。
        RealmResults<TableName> result = query.findAll();
        int size = result.size();
        String text = "";
        // 以迴圈訪問所有查詢出的資料。
        for (int i = 0; i < size; i++) {
            TableName item = result.get(i);
            text += item.getFieldName() + "\n";
        }

        // 顯示結果
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```