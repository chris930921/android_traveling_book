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

        Bundle argument = getIntent().getExtras();
        String valueOne = argument.getString("KeyNameOne");
        int valueTwo = argument.getInt("KeyNameTwo");
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

## 從第一個 Activity 移動到第二個 Activity
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
                Bundle argument = new Bundle();
                argument.putString("KeyNameOne","String Text");
                argument.putInt("KeysNameTwo",100);
                argument.putFloat("KeyNameTwo",100.0F);

                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                goOtherActivity.putExtras(argument);
                activity.startActivity(goOtherActivity);
            }
        });
    }
}
```
