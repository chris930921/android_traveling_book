# Activity 換頁後回傳資訊

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
    private Activity activity;
    private int returnValue;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;
        returnValue = (int) (Math.random() * 100);

        Button backPage = new Button(this);
        backPage.setText("回傳 " + returnValue);
        setContentView(backPage);

        backPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                //建立包裹，放入回傳值。
                Bundle argument = new Bundle();
                argument.putInt("returnValueName", returnValue);

                //取出上一個Activity傳過來的 Intent 物件。
                Intent intent = getIntent();
                //放入要回傳的包裹。
                intent.putExtras(argument);

                //設定回傳狀態。
                setResult(Activity.RESULT_OK, intent);
                finish();
            }
        });
    }
}

```

## 從第一個 Activity 移動到第二個 Activity
```java
public class MainActivity extends Activity {
    private Activity activity;
    private Button toNextPage;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;
        toNextPage = new Button(this);
        setContentView(toNextPage);

        toNextPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                // 要讓其他 Activity 回傳值，必須用 startActivityForResult 方法開啟。
                activity.startActivityForResult(goOtherActivity, 0);
            }
        });
    }


    @Override // 覆寫 onActivityResult，傳值回來時會執行此方法。
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (resultCode == Activity.RESULT_OK) {
            //將包裹從 Intent 中取出。
            Bundle argument = data.getExtras();
            //將回傳值用指定的 key 取出，並從整數轉為字串。
            String value = String.valueOf(argument.getInt("returnValueName"));
            toNextPage.setText("取得:" + value);
        }
    }
}

```
