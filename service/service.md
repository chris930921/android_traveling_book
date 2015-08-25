# Service 將自己本身關閉

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
    // 計數用屬性
    private int count;
    // 定時器，因為會在不同環境中，分別使用定時器的 cancel()、schedule() 方法，
    // 所以放到類別屬性中提升物件可見度。
    private Timer timer;

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        // 屬性初始化
        count = 0;

        TimerTask action = new TimerTask() {
            @Override
            public void run() {

                if (count < 3) {
                    // 還沒數到 3 ，顯示數值並 + 1 。
                    Log.d("MainService", "次數: " + count);
                    count = count + 1;

                } else {
                    // 已經數到 3，關閉定時器，Service 自行關閉。
                    Log.d("MainService", "結束背景服務。");
                    // 利用定時器的 cancel() 方法，停止定時動作。
                    timer.cancel();
                    // 利用 Service 自帶的 stopSelf() 方法，將自己關閉。
                    stopSelf();

                }
            }
        };

        // 建立定時器物件，放入可見範圍較高的類別屬性中。
        // 如果放入區域變數中，在數到 3 時會找不到定時器物件執行 cancel() 方法。
        timer = new Timer();
        timer.schedule(action, 1000, 1000);
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }
}
```
