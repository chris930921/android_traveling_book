# 讀取資料範例

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //設定資料來源名稱
        String fileName = "save_file";
        //利用名稱取得SharedPreferences物件，設定為多程序讀取同一個資料來源。
        SharedPreferences sharedPreferences = getSharedPreferences(fileName, Context.MODE_MULTI_PROCESS);

        //利用KeyNameOne名稱取得字串，如果沒有Value則取預設值Nothing。
        String valueOne = sharedPreferences.getString("KeyNameOne", "Nothing");
        //利用KeyNameTwo名稱取得字串，如果沒有Value則取預設值0。
        int valueTwo = sharedPreferences.getInt("KeyNameTwo", 0);
        //利用KeyNameThree名稱取得字串，如果沒有Value則取預設值0.0F。
        float valueThree = sharedPreferences.getFloat("KeyNameThree", 0.0F);
        //利用KeyNameFour名稱取得字串，如果沒有Value則取預設值0L。
        long valueFour = sharedPreferences.getLong("KeyNameFour", 0L);
        //利用KeyNameFive名稱取得字串，如果沒有Value則取預設值false。
        boolean vlaueFive = sharedPreferences.getBoolean("KeyNameFive", false);

        //將結果輸出成字串
        String result = valueOne + "\n" +
                valueTwo + "\n" +
                valueThree + "\n" +
                valueFour + "\n" +
                vlaueFive + "\n";

        TextView v = new TextView(this);
        v.setText(result);
        //設定介面
        setContentView(v);
    }
}

```
