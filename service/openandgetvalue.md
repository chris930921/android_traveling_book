# OpenAndGetValue開啟並傳送資訊

#### AndroidManifest.xml 註冊 Service 標籤
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.ceph.monitor.service">

    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme">
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!--新增 Service -->
        <service android:name=".MainService" />
    </application>

</manifest>
```

#### MainActivity.java
```java
public class MainActivity extends ActionBarActivity {
    Activity activity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;

        //新增包裹放入資料。
        Bundle message = new Bundle();
        message.putString("KeyOne", "ValueOne");

        //放入intent中，將資料一起傳送出去。
        Intent intent = new Intent(activity, MainService.class);
        intent.putExtras(message);
        startService(intent);
    }
}
```


#### MainService.java
```java
public class MainService extends Service {

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        // 從參數傳入的 intent 中取回包裹。
        Bundle message = intent.getExtras();
        // 用相同的 Key 字串取出資料。
        String value = message.getString("KeyOne");
        // 顯示。
        Toast.makeText(this, value, Toast.LENGTH_LONG).show();
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```
