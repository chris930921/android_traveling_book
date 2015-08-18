# ArrayList

* 一種資料結構。
* Java 中可動態增加元素的陣列。
* 需決定放置的元素的型態。
* toString() 方法可將陣列中的所有元素以字串呈現。
* add() 方法放入元素。
* get() 方法取得元素，索引值從 0 開始。

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //動態儲存 String 字串的陣列。
        ArrayList<String> strGroup = new ArrayList<>();
        strGroup.add("String One");
        strGroup.add("String Two");
        strGroup.add("String Three");

        //動態儲存 Int 數值的陣列。
        ArrayList<Integer> intGroup = new ArrayList<>();
        intGroup.add(1);
        intGroup.add(2);
        intGroup.add(3);

        //動態儲存 Float 數值的陣列。
        ArrayList<Float> floatGroup = new ArrayList<>();
        floatGroup.add(1F);
        floatGroup.add(2F);
        floatGroup.add(3F);

        //動態儲存 Boolean 數值的陣列。
        ArrayList<Boolean> booleanGroup = new ArrayList<>();
        booleanGroup.add(true);
        booleanGroup.add(false);
        booleanGroup.add(true);

        //動態儲存 TextView 物件的陣列。
        ArrayList<TextView> textViewGroup = new ArrayList<>();
        textViewGroup.add(new TextView(this));
        textViewGroup.add(new TextView(this));
        textViewGroup.add(new TextView(this));

        //顯示結果
        String result = strGroup.toString() + "\n\n" +
                intGroup.toString() + "\n\n" +
                floatGroup.toString() + "\n\n" +
                booleanGroup.toString() + "\n\n" +
                textViewGroup.toString() + "\n\n";

        TextView v = new TextView(this);
        v.setText(result);
        //設定介面
        setContentView(v);
    }
}
```

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        ArrayList<String> strGroup = new ArrayList<>();
        strGroup.add("String One");
        strGroup.add("String Two");
        strGroup.add("String Three");

        //取出元素
        String result = strGroup.get(0) + "\n" +
                strGroup.get(1) + "\n" +
                strGroup.get(2) + "\n";

        TextView v = new TextView(this);
        v.setText(result);
        setContentView(v);
    }
}

```
