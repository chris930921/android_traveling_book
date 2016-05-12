# 查詢條件 - 排序結果

User.java
```java
public class User extends RealmObject {
    private int id;
    private String name;

    public void setId(int id) { this.id = id; }
    public int getId() { return id; }

    public void setName(String name) { this.name = name; }
    public String getName() { return name; }
}
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    @RealmModule(classes = {User.class})
    public static class Module {}

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        RealmConfiguration config = new RealmConfiguration.Builder(this)
                .name("database_name.realm")
                .setModules(new Module())
                        // 如上次以建立過相同名稱資料庫，但欄位結構已經改變時，會刪除舊資料庫，不是實務上的必要動作。
                .deleteRealmIfMigrationNeeded()
                .build();
        Realm realm = Realm.getInstance(config);

        realm.beginTransaction();
        // 這裡清空資料表，只是為了保持乾淨讓執行結果正常，不是實務上的必要動作。
        realm.clear(User.class);
        for (int i = 0; i < 10; i++) {
            User item = new User();
            item.setId(i);
            // 這裡故意將名稱的序號弄反，測試排序結果。
            item.setName((10 - i) + "");
            realm.copyToRealmOrUpdate(item);
        }
        realm.commitTransaction();

        final String NAME = "name";
        // 根據名稱作小到大的排序
        String text = realm.where(User.class).findAllSorted(NAME, Sort.ASCENDING).toString() + "\n\n\n";
        // 根據名稱作大到小的排序
        text += realm.where(User.class).findAllSorted(NAME, Sort.DESCENDING).toString();
        // 顯示結果。
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```