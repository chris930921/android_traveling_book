# HashMap

* 一種資料結構。
*  Key-Value 的形式儲存資料。
* 需決定Key的型態和Value的型態。
* 透過 put( Key, Value ) 儲存。
* 透過 get( Key ) 取得 Value。

#### 用 Key 儲存。
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // Key 是 String 型態，Value 是 String 型態。
        HashMap<String, String> mapOne = new HashMap<>();
        mapOne.put("KeyOne", "ValueOne");
        mapOne.put("KeyTwo", "ValueTwo");

        // Key 是 String 型態，Value 是 Int 型態。
        HashMap<String, Integer> mapTwo = new HashMap<>();
        mapTwo.put("KeyOne", 10101010);
        mapTwo.put("KeyTwo", 20202020);

        // Key 是 Int 型態，Value 是 String 型態。
        HashMap<Integer, String> mapThree = new HashMap<>();
        mapThree.put(60, "MapThreeValueOne");
        mapThree.put(100, "MapThreeValueTwo");

        String result = mapOne.toString() + "\n" +
                mapTwo.toString() + "\n" +
                mapThree.toString() + "\n";

        TextView v = new TextView(this);
        v.setText(result);
        setContentView(v);
    }
}
```

#### 用 Key 取值
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        HashMap<String, String> mapOne = new HashMap<>();
        mapOne.put("KeyOne", "ValueOne");
        mapOne.put("KeyTwo", "ValueTwo");

        HashMap<String, Integer> mapTwo = new HashMap<>();
        mapTwo.put("KeyOne", 10101010);
        mapTwo.put("KeyTwo", 20202020);

        HashMap<Integer, String> mapThree = new HashMap<>();
        mapThree.put(60, "MapThreeValueOne");
        mapThree.put(100, "MapThreeValueTwo");

        //用字串取字串
        String mapOneValue = mapOne.get("KeyOne");
        //用字串取數字
        int mapTwoValue = mapTwo.get("KeyOne");
        //用數字取字串
        String mapThreeValue = mapThree.get(60);

        String result = mapOneValue + "\n" +
                mapTwoValue + "\n" +
                mapThreeValue + "\n";

        TextView v = new TextView(this);
        v.setText(result);
        setContentView(v);
    }
}

```

#### 用物件當 Key ，進行儲存和讀取
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Object objectOne = new Object();
        Object objectTwo = new Object();
        Object objectThree = new Object();

        // Key 是 Object 型態，Value 是 String 型態。
        HashMap<Object, String> mapOne = new HashMap<>();
        mapOne.put(objectOne, "ValueOne");
        mapOne.put(objectTwo, "ValueTwo");
        mapOne.put(objectThree, "ValueThree");

        String result = mapOne.get(objectOne) + "\n" +
                mapOne.get(objectTwo) + "\n" +
                mapOne.get(objectThree) + "\n";

        TextView v = new TextView(this);
        v.setText(result);
        setContentView(v);
    }
}
```

