# 在 Broadcast 中傳送訊息

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
                // 利用 intent 參數取得包裹。
                Bundle message = intent.getExtras();
                // 用相同 Key 取得資料。
                String value = message.getString("KeyOne");
                text.setText(value);
            }
        };

        final String Action = "FilterStringOne";
        IntentFilter filter = new IntentFilter(Action);
        registerReceiver(receiver, filter);

        new Timer().schedule(new TimerTask() {
            @Override
            public void run() {
                // 建立包裹，放入資料。
                Bundle message = new Bundle();
                message.putString("KeyOne", "ValueOne");

                Intent intent = new Intent(Action);
                // 將包裹放到 intent 中。
                intent.putExtras(message);
                sendBroadcast(intent);
            }
        }, 2000);
    }
}
```
