# 生命週期

### onCreate
* Service 從關閉到開啟時會執行。
* 整個生命週期只執行一次。

### onStartCommand
* Service 從關閉到開啟會執行。
* Service 開啟中執行 startService() 會再執行一次。
* 整個生命週期可能會執行多次。

### onDestory
* Service 從開啟到關閉時會執行。
* 整個生命週期只執行一次。

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

        Button v = new Button(this);
        v.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(activity, MainService.class);
                startService(intent);
            }
        });
        setContentView(v);
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Intent intent = new Intent(activity, MainService.class);
        stopService(intent);
    }
}
```

#### MainService.java
```java
import android.app.Service;
import android.content.Intent;
import android.os.IBinder;
import android.util.Log;

public class MainService extends Service {

    @Override
    public void onCreate() {
        Log.d("MainService", "onCreate");
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        Log.d("MainService", "onStartCommand");
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onDestroy() {
        Log.d("MainService", "onDestroy");
    }

    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```
