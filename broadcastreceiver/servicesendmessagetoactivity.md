# Service 發送訊息給 Activity

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
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        final TextView text = new TextView(this);
        setContentView(text);

        BroadcastReceiver receiver = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                // 處理 Service 傳來的訊息。
                Bundle message = intent.getExtras();
                int value = message.getInt("KeyOne");
                String strValue = String.valueOf(value);
                text.setText(strValue);
            }
        };

        final String Action = "FilterString";
        IntentFilter filter = new IntentFilter(Action);
        // 將 BroadcastReceiver 在 Activity 掛起來。
        registerReceiver(receiver, filter);

        // 啟動 Service。
        Intent intent = new Intent(this, MainService.class);
        startService(intent);
    }
}
```

#### MainService.java
```java
public class MainService extends Service {
    int count = 0;

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        TimerTask action = new TimerTask() {
            @Override
            public void run() {
                // 每隔 1 秒就將計數 + 1，並發送廣播。
                Bundle message = new Bundle();
                message.putInt("KeyOne", count);
                Intent intent = new Intent("FilterString");
                intent.putExtras(message);
                sendBroadcast(intent);

                count++;
            }
        };

        Timer timer = new Timer();
        timer.schedule(action, 1000, 1000);
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```
