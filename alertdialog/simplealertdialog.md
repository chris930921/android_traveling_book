# AlertDialog 快速範例

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //建立 AlertDialog.Builder 物件，利用方法鍊設定視窗。
        new AlertDialog.Builder(this)
                // 設定標題圖片
                .setIcon(R.drawable.ic_launcher)
                // 設定標題文字
                .setTitle("標題")
                // 設定視窗內容
                .setMessage("內容")
                // 設定正邊按鈕，按下顯示 Toast
                .setPositiveButton("正邊按鈕", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        Toast.makeText(getApplicationContext(), "按了正邊", Toast.LENGTH_SHORT).show();
                    }
                })
                // 設定中間按鈕，按下顯示 Toast
                .setNeutralButton("中間按鈕", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        Toast.makeText(getApplicationContext(), "按了中間", Toast.LENGTH_SHORT).show();
                    }
                })
                // 設定反邊按鈕，按下顯示 Toast
                .setNegativeButton("反邊按鈕", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        Toast.makeText(getApplicationContext(), "按了反邊", Toast.LENGTH_SHORT).show();
                    }
                })
                // 設定完畢，顯示視窗
                .show();
    }
}
```
