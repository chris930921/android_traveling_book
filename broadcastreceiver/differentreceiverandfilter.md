# 註冊多個接收器，使用不同過濾器

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

        // 建立接收器 1 號，用 FilterString 過濾。
        BroadcastReceiver receiverOne = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                textOne.setText("textOne changed");
            }
        };
        // 建立過濾器 1 號。
        final String ActionOne = "FilterStringOne";
        IntentFilter filterOne = new IntentFilter(ActionOne);
        registerReceiver(receiverOne, filterOne);


        // 建立接收器 2 號，用 FilterString 過濾。
        BroadcastReceiver receiverTwo = new BroadcastReceiver() {
            @Override
            public void onReceive(Context context, Intent intent) {
                textTwo.setText("textTwo changed");
            }
        };
        // 建立過濾器 2 號
        final String ActionTwo = "FilterStringTwo";
        IntentFilter filterTwo = new IntentFilter(ActionTwo);
        registerReceiver(receiverTwo, filterTwo);


        // 延遲兩秒發送 ActionOne 的廣播。
        new Timer().schedule(new TimerTask() {
            @Override
            public void run() {
                Intent intent = new Intent(ActionOne);
                sendBroadcast(intent);
            }
        }, 2000);

        // 延遲五秒發送 ActionTwo 的廣播。
        new Timer().schedule(new TimerTask() {
            @Override
            public void run() {
                Intent intent = new Intent(ActionTwo);
                sendBroadcast(intent);
            }
        }, 5000);
    }
}
```
