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

        //第二個 Activity 的顯示內容。
        TextView showText = new TextView(this);
        showText.setText("OtherActivity");
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
                // Android 將意圖這個概念包裝成一個類別，用來將 Activity 或 Service 以指定的方式開啟。
                Intent goOtherActivity;
                // 第一個參數放入現在的 Activity。
                // 第二個參數是 Activty 類別的 class 物件，指定要進入的 Activty 是哪一個。
                goOtherActivity = new Intent(activity, OtherActivity.class);
                // 啟動另一個 Actiity。
                activity.startActivity(goOtherActivity);
            }
        });
    }
}
```
