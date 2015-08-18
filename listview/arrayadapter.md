# ArrayAdapter

#### android.R.layout.simple_list_item_1  文字樣式，上下間距適中
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //將要顯示的項目放進字串陣列
        String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        //利用字串陣列製作 Adapter ，顯示樣式為 android.R.layout.simple_list_item_1。
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
            this,
            android.R.layout.simple_list_item_1,
            strGroup);

        // 如果用XML排版  ListView v = (ListView) findViewById(R.id.元件名稱);
        ListView v = new ListView(this);
        //將 Adapter 放進元件中，設定資料來源。
        v.setAdapter(adapter);
        setContentView(v);
    }
}
```

#### android.R.layout.simple_list_item_1  文字樣式，上下間距較小
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                //換樣式
                android.R.layout.simple_spinner_item,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
}
```

#### android.R.layout.simple_list_item_1  文字樣式，上下間距較小，文字較大
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                //換樣式
                android.R.layout.simple_gallery_item,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
}
```

#### android.R.layout.simple_list_item_single_choice  單選樣式
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                //換樣式
                android.R.layout.simple_list_item_single_choice,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
}
```

#### android.R.layout.simple_list_item_multiple_choice  多選樣式
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String[] strGroup = {"字串1", "字串2", "字串3", "字串4", "字串5", "字串6"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                //換樣式
                android.R.layout.simple_list_item_multiple_choice,
                strGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
```

