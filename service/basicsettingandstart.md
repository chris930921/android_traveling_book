# 基本設定與開啟

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
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 意圖開啟 Service
        Intent intent = new Intent(this, MainService.class);
        startService(intent);
    }
}

```

#### 新增 MainService.java 類別
```java
import android.app.Service;
import android.content.Intent;
import android.os.IBinder;
import android.widget.Toast;

public class MainService extends Service {
    @Override
    public void onCreate() {
        //在 Service 開啟時顯示訊息。
        Toast.makeText(this, "onCreate", Toast.LENGTH_LONG).show();
    }


    @Override // 目前還不會用到的方法，先不管。
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```

