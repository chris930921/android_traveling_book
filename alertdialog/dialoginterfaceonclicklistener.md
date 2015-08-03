# AlertDialog OnClickListener 方法分析

### 方法簽名
```java
    public void onClick(DialogInterface dialogInterface, int which)
```

### dialogInterface 參數，代表視窗物件本身，可以改變視窗的設定。
```java
public class MainActivity extends Activity {
    private AlertDialog dialog;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //先建立 OnClickListener 物件，並設定好按下後執行的程式。
        DialogInterface.OnClickListener event = new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int which) {
                //強轉型態成為 AlertDialog 物件。
                AlertDialog dialog = (AlertDialog) dialogInterface;
                dialog.setTitle("按下後變更了標題");
            }
        };

        //建立視窗
        dialog = new AlertDialog.Builder(this)
                .setTitle("標題")
                // 將 OnClickListener 物件加入到參數中，設定觸發事件。
                .setPositiveButton("正邊按鈕", event)
                .show();

        //建立畫面
        Button button = new Button(this);
        button.setText("顯示視窗");
        setContentView(button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                dialog.show();
            }
        });
    }
}
```

### which 參數，用來判斷使用者按下哪個按鈕。
```java
public class MainActivity extends Activity {
    private AlertDialog dialog;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //先建立 OnClickListener 物件，並設定好按下後執行的程式。
        DialogInterface.OnClickListener event = new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int which) {
                // 利用 which 判斷是否與 BUTTON_POSITIVE 相等，相等表示使用者按下正邊按鈕
                if (which == AlertDialog.BUTTON_POSITIVE) {
                    Toast.makeText(getApplicationContext(), "按了正邊", Toast.LENGTH_SHORT).show();
                }// 利用 which 判斷是否與 BUTTON_NEUTRAL 相等，相等表示使用者按下中間按鈕
                else if (which == AlertDialog.BUTTON_NEUTRAL) {
                    Toast.makeText(getApplicationContext(), "按了中間", Toast.LENGTH_SHORT).show();
                }// 利用 which 判斷是否與 BUTTON_NEGATIVE 相等，相等表示使用者按下反邊按鈕
                else if (which == AlertDialog.BUTTON_NEGATIVE) {
                    Toast.makeText(getApplicationContext(), "按了反邊", Toast.LENGTH_SHORT).show();
                }
            }
        };

        //建立視窗
        dialog = new AlertDialog.Builder(this)
                .setTitle("標題")
                        // 將 OnClickListener 物件加入到參數中，設定觸發事件。
                .setPositiveButton("正邊按鈕", event)
                .setNeutralButton("中間按鈕", event)
                .setNegativeButton("反邊按鈕", event)
                .show();

        //建立畫面
        Button button = new Button(this);
        button.setText("顯示視窗");
        setContentView(button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                dialog.show();
            }
        });
    }
}
```

