# Activity 換頁


## AndroidManifest.xml 註冊 Activity
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.chriske" >

    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity
            android:name=".OtherActivity"
            android:label="@string/app_name"/>

    </application>
</manifest>
```


## 建立第二個 Activity

```java
public class OtherActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //從 Intent 取出包裹
        Bundle argument = getIntent().getExtras();
        //透過 key 取出字串
        String valueOne = argument.getString("KeyNameOne");
        //透過 key 取出整數
        int valueTwo = argument.getInt("KeyNameTwo");
        //透過 key 取出浮點數
        float valueThree = argument.getFloat("KeyNameThree");

        TextView showText = new TextView(this);
        showText.setText(
            valueOne + " : ",
            valueTwo + " : ",
            valueThree);
        setContentView(showText);
    }
}

```

## 將訊息放再 Bundle 後，從第一個 Activity 移動到第二個 Activity
```java
public class MainActivity extends Activity {
    private Activity activity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        activity = this;

        Button toNextPage = new Button(this);
        setContentView(toNextPage);

        toNextPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //建立包裹
                Bundle argument = new Bundle();
                //放入字串，key 取名 KeyNameOne
                argument.putString("KeyNameOne","String Text");
                //放入整數，key 取名 KeysNameTwo
                argument.putInt("KeysNameTwo",100);
                //放入浮點數，key 取名 KeyNameTwo
                argument.putFloat("KeyNameTwo",100.0F);

                //建立 Intent 物件，意圖開啟其他 Activity。
                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                //將包裹放入 Intent 中。
                goOtherActivity.putExtras(argument);
                activity.startActivity(goOtherActivity);
            }
        });
    }
}
```
