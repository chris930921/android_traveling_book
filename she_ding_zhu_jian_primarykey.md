# 設定主鍵 PrimaryKey

User.java
```java
public class User extends RealmObject {
    // 設定 id 欄位為資料表的主鍵，其值將不可以重複。
    @PrimaryKey
    private int id;
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
            // 這裡如果使用 realm.createObject() 方法，將會因為類別初始化時，int 欄位初始值都為 0 ，導致主鍵重複而使 APP 崩潰。
            // 如對有主鍵的資料表做新增時，建議先建立物件然後修改主鍵的數值，再使用  realm.copyToRealmOrUpdate() 寫入資料表。
            User item = new User();
            item.setId(i);
            realm.copyToRealmOrUpdate(item);
        }
        realm.commitTransaction();

        // 顯示結果。
        String text = realm.where(User.class).findAll().toString();
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```