# 背景執行範例

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

        //開啟 Service
        Intent intent = new Intent(activity, MainService.class);
        startService(intent);
    }
}
```


#### MainService.java
```java
public class MainService extends Service {

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        // 設定每次時間觸發時執行的動作，將這些動作包成物件，放進 TimerTask 型態的參考中。
        TimerTask action = new TimerTask() {
            @Override
            public void run() {
                Log.d("MainService", "Running");
            }
        };

        // 將計時器物件建立出來。
        Timer timer = new Timer();
        // 利用 schedule() 方法，將執行動作、延遲時間(1秒)、間隔時間(1秒) 輸入方法中。
        // 執行此方法後將會定時執行動作。
        timer.schedule(action, 1000, 1000);
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```
