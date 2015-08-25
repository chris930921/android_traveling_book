# 註冊多個接收器，使用同一種過濾器

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // 建立畫面
        final TextView textOne = new TextView(this);
        final TextView textTwo = new TextView(this);
        LinearLayout container = new LinearLayout(this);
        container.setOrientation(LinearLayout.VERTICAL);
        container.addView(textOne);
        container.addView(textTwo);
        setContentView(container);

        // 建立過濾器。
        final String Action = "FilterString";
        IntentFilter filter = new IntentFilter(Action);

        // 建立接收器 1 號，用 FilterString 過濾。
        BroadcastReceiver receiverOne = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                // 改變第一行的內容
                textOne.setText("textOne changed");
            }
        };
        registerReceiver(receiverOne, filter);

        // 建立接收器 2 號，用 FilterString 過濾。
        BroadcastReceiver receiverTwo = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                // 改變第二行的內容
                textTwo.setText("textTwo changed");
            }
        };
        registerReceiver(receiverTwo, filter);

        // 延遲兩秒執行。
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
