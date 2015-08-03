# AlertDialog 快速範例拆解

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 建立 Dialog Builder 物件。
        AlertDialog.Builder builder = new AlertDialog.Builder(this);

        // 透過 Builder 物件提供的方法設定視窗。
        builder.setIcon(R.drawable.ic_launcher);
        builder.setTitle("標題");
        builder.setMessage("內容");

        // Listener 設定為 null，表示按下後不做任何動作。
        builder.setPositiveButton("正邊按鈕", null);
        builder.setNeutralButton("中間按鈕", null);
        builder.setNegativeButton("反邊按鈕", null);

        // Builder 物件提供的顯示方法，會回傳一個 AlertDialog 視窗物件。
        AlertDialog dialog = builder.show();
    }
}
```

### 方法簽名
* 方法修飾詞 **方法回傳型態** 方法名稱 (方法參數)
*  public **AlertDialog.Builder** setIcon(int iconId)
*  public **AlertDialog.Builder** setTitle(java.lang.CharSequence title)
*  public **AlertDialog.Builder** setMessage(java.lang.CharSequence message)
*  public **AlertDialog.Builder** setPositiveButton(CharSequence text,OnClickListener listener)
*  public **AlertDialog.Builder** setNeutralButton(CharSequence text,OnClickListener listener)
*  public **AlertDialog.Builder** setNegativeButton(CharSequence text,OnClickListener listener)
*  public **AlertDialog** show()

### 說明
* Builder 物件的設定方法都會回傳 Builder 物件本身。
* 利用方法回傳物件本身的特性，就可透過方法鍊的方式進行設定。
* 利用 show 方法回傳的 AlertDialog 物件，可以再進行設定或是顯示。
