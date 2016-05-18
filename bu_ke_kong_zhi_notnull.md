# 不可空值 NotNull

User.java
```java
public class User extends RealmObject {
    private int id;
    // 設定 name 欄位不可為空值(Null)。
    @Required
    private String name;

    public void setId(int id) {this.id = id;}
    public int getId() {return id;}

    public void setName(String name) {this.name = name;}
    public String getName() {return name;}
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
                // 如上次以建立過相同名稱資料庫，但欄位結構已經改變時，會刪除舊資料庫，不是實務上的必要
                .deleteRealmIfMigrationNeeded()
                .setModules(new Module())
                .build();
        Realm realm = Realm.getInstance(config);

        realm.beginTransaction();
        // 這裡清空資料表，只是為了保持乾淨讓執行結果正常，不是實務上的必要動作。
        realm.clear(User.class);
        for (int i = 0; i < 10; i++) {
            User item = realm.createObject(User.class);
            item.setId(i);
            // 程式崩潰，因 name 不可設定為 Null。
            item.setName(null);
        }
        realm.commitTransaction();
    }
}
```