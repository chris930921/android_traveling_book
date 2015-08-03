# Activity 換頁後回傳資訊並判斷請求類型

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


## 建立第二個 Activity，只用來測試請求編號，不做功能。

```java
public class OtherActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Button backPage = new Button(this);
        backPage.setText("回到上一頁。");
        setContentView(backPage);

        backPage.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                finish();
            }
        });
    }
}
```

## 從第一個 Activity 移動到第二個 Activity時帶入不同編號，回傳時判斷請求編號。
```java
public class MainActivity extends Activity {
    private Activity activity;
    private TextView showMessage;
    private Button requestOne;
    private Button requestTwo;
    //定義不同的請求編號。
    public static final int REQUEST_ONE_CODE = 0;
    public static final int REQUEST_TWO_CODE = 1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;
        //設定元件內容。
        showMessage = new TextView(this);
        requestOne = new Button(this);
        requestOne.setText("第一種請求，requestCode: " + REQUEST_ONE_CODE);
        requestTwo = new Button(this);
        requestTwo.setText("第二種請求。requestCode: " + REQUEST_TWO_CODE);

        //設定垂直排列框架，並放入元件。
        LinearLayout container = new LinearLayout(this);
        container.setOrientation(LinearLayout.VERTICAL);
        container.addView(showMessage);
        container.addView(requestOne);
        container.addView(requestTwo);
        setContentView(container);

        //用不同的請求編號打開其他 Activity。
        requestOne.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                //編號 REQUEST_ONE_CODE
                activity.startActivityForResult(goOtherActivity, REQUEST_ONE_CODE);
            }
        });
        requestTwo.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent goOtherActivity = new Intent(activity, OtherActivity.class);
                //編號 REQUEST_TWO_CODE
                activity.startActivityForResult(goOtherActivity, REQUEST_TWO_CODE);
            }
        });
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        //利用第一個 requestCode 參數回傳的值，判斷剛剛的請求編號是多少，來做對應的介面設定。
        if (requestCode == REQUEST_ONE_CODE) {
            showMessage.setText("第一種請求: REQUEST_ONE_CODE");
        } else if (requestCode == REQUEST_TWO_CODE) {
            showMessage.setText("第二種請求: REQUEST_TWO_CODE");
        }
    }
}
```
