# SimpleAdapter

#### simple_list_item_2 樣式，標題字體大，內容字體小。

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //設定欄位名稱
        String fieldOne = "field 1";
        String fieldTwo = "field 2";

        //Key放欄位名稱，Value放每個項目的內容
        HashMap<String, String> itemOne = new HashMap<>();
        itemOne.put(fieldOne, "標題 1");
        itemOne.put(fieldTwo, "內容 1");

        HashMap<String, String> itemTwo = new HashMap<>();
        itemTwo.put(fieldOne, "標題 2");
        itemTwo.put(fieldTwo, "內容 2");

        HashMap<String, String> itemThree = new HashMap<>();
        itemThree.put(fieldOne, "標題 3");
        itemThree.put(fieldTwo, "內容 3");

        //將每個項目放到 List 中。
        ArrayList<HashMap<String, String>> itemGroup = new ArrayList<>();
        itemGroup.add(itemOne);
        itemGroup.add(itemTwo);
        itemGroup.add(itemThree);

        // fieldOne 欄位的內容會放到 android.R.layout.simple_list_item_2 的 android.R.id.text1 元件上。
        // fieldTwo 欄位的內容會放到 android.R.layout.simple_list_item_2 的 android.R.id.text2 元件上。
        String[] fieldNameGroup = {fieldOne, fieldTwo};
        int[] fieldIdGroup = {android.R.id.text1, android.R.id.text2};

        // 放入以上參數，製作 Adapter。
        SimpleAdapter adapter = new SimpleAdapter(
                this,
                itemGroup,
                android.R.layout.simple_list_item_2,
                fieldNameGroup,
                fieldIdGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
}

```

#### two_line_list_item 樣式，標題內容字體一樣大。

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //設定欄位名稱
        String fieldOne = "field 1";
        String fieldTwo = "field 2";

        //Key放欄位名稱，Value放每個項目的內容
        HashMap<String, String> itemOne = new HashMap<>();
        itemOne.put(fieldOne, "標題 1");
        itemOne.put(fieldTwo, "內容 1");

        HashMap<String, String> itemTwo = new HashMap<>();
        itemTwo.put(fieldOne, "標題 2");
        itemTwo.put(fieldTwo, "內容 2");

        HashMap<String, String> itemThree = new HashMap<>();
        itemThree.put(fieldOne, "標題 3");
        itemThree.put(fieldTwo, "內容 3");

        //將每個項目放到 List 中。
        ArrayList<HashMap<String, String>> itemGroup = new ArrayList<>();
        itemGroup.add(itemOne);
        itemGroup.add(itemTwo);
        itemGroup.add(itemThree);

        // fieldOne 欄位的內容會放到 android.R.layout.two_line_list_item 的 android.R.id.text1 元件上。
        // fieldTwo 欄位的內容會放到 android.R.layout.two_line_list_item 的 android.R.id.text2 元件上。
        String[] fieldNameGroup = {fieldOne, fieldTwo};
        int[] fieldIdGroup = {android.R.id.text1, android.R.id.text2};

        // 放入以上參數，製作 Adapter。
        SimpleAdapter adapter = new SimpleAdapter(
                this,
                itemGroup,
                android.R.layout.two_line_list_item,
                fieldNameGroup,
                fieldIdGroup);

        ListView v = new ListView(this);
        v.setAdapter(adapter);
        setContentView(v);
    }
}


```
