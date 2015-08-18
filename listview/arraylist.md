# ArrayList

* Java 中用來當作動態的陣列

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
