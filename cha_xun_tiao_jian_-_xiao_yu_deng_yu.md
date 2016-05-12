# 查詢條件 - 統計資料

TableName.java
```java
public class User extends RealmObject {
    private int id;
    private String name;

    public void setId(int id) {
        this.id = id;
    }

    public int getId() {
        return id;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    @RealmModule(classes = {User.class})
    public static class Module {
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        RealmConfiguration config = new RealmConfiguration.Builder(this)
                .name("database_name.realm")
                .setModules(new Module())
                // 如之前有建立過相同資料庫，但資料表結構已改變時，將舊的資料移除。
                .deleteRealmIfMigrationNeeded()
                .build();
        Realm realm = Realm.getInstance(config);
        realm.beginTransaction();
        for (int i = 0; i < 10; i++) {
            User item = realm.createObject(User.class);
            item.setId(i);
        }
        realm.commitTransaction();

        final String ID = "id";

        String text = "";
        // ID 所有的總和。
        text += realm.where(User.class).sum(ID).intValue() + "\n";
        // ID 所有的平均。
        text += realm.where(User.class).average(ID) + "\n";
        // 資料表所有資料筆數。
        text += realm.where(User.class).count() + "\n";
        // ID 中的最大值。
        text += realm.where(User.class).max(ID) + "\n";
        // ID 中的最小值。
        text += realm.where(User.class).min(ID) + "\n";

        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```