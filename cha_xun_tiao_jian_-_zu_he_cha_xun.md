# 查詢條件 - 組合查詢

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
    public static class Module {
    }

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
            User item = realm.createObject(User.class);
            item.setId(i);
        }
        realm.commitTransaction();

        final String ID = "id";
        String text = "";
        // 查詢條件 ID == 2 or ID == 3
        text += realm.where(User.class).equalTo(ID, 2).or().equalTo(ID, 3).findAll().toString();
        text += "\n\n\n";
        // 查詢條件 ID > 2 and ID < 8
        text += realm.where(User.class).greaterThan(ID, 2).lessThan(ID, 8).findAll().toString();

        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```