# 最簡形式範例

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // 建立 TextView 元件。
        final TextView text = new TextView(this);
        // 放入介面中。
        setContentView(text);

        // 建立BroadcastReceiver 物件，在物件中設定收到廣播的執行動作。
        BroadcastReceiver receiver = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                // 設定 TextView 內容。
                text.setText("Received Message !");
            }
        };

        // 設定 ACTION 的過濾內容。
        final String Action = "FilterStringOne";
        // 建立 IntentFilter 過濾器，並將 ACTION 放進建構式的參數中。
        IntentFilter filter = new IntentFilter(Action);
        // 使用 Activity 提供的 registerReceiver() 方法動態註冊廣播。
        registerReceiver(receiver, filter);

        // 利用定時器，延遲兩秒後發送廣播。
        new Timer().schedule(new TimerTask() {
            @Override
            public void run() {
                // 在 intent 的建構式中指定 ACTION。
                Intent intent = new Intent(Action);
                // 利用 Activity 提供的 sendBroadcast() 方法發送廣播。
                sendBroadcast(intent);
            }
        }, 2000);
    }
}
```
