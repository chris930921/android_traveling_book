# Activity 換頁後回傳資訊並判斷狀態

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


## 建立第二個 Activity，根據數值決定狀態。

```java
public class OtherActivity extends Activity {
    private int returnValue;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        returnValue = (int) (Math.random() * 100);

        Button backPage = new Button(this);
        backPage.setText("偶數回傳RESULT_OK，奇數回傳RESULT_CANCELED");
        setContentView(backPage);

        backPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //使用 MOD 2 判斷奇偶數，並決定回傳狀態。
                if (returnValue % 2 == 0) {
                    setResult(Activity.RESULT_OK, getIntent());
                } else {
                    setResult(Activity.RESULT_CANCELED, getIntent());
                }
                finish();
            }
        });
    }
}

```

## 從第一個 Activity 移動到第二個 Activity 產生隨機數，回傳時利用狀態判斷是否偶數。
```java
public class MainActivity extends Activity {
    private Activity activity;
    private Button toNextPage;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;
        toNextPage = new Button(this);
        toNextPage.setText("進入到下一個Activity，產生隨機數。");
        setContentView(toNextPage);

        toNextPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                activity.startActivityForResult(goOtherActivity, 0);
            }
        });
    }

    @Override // 覆寫 onActivityResult，傳值回來時會執行此方法。
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (resultCode == Activity.RESULT_OK) {
            toNextPage.setText("隨機取得偶數成功。");
        } else if (resultCode == Activity.RESULT_CANCELED) {
            toNextPage.setText("隨機取得偶數失敗。");
        }
    }
}
```
