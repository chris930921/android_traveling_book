# AlertDialog 先建立後顯示

```java
public class MainActivity extends Activity {
    private AlertDialog dialog;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("標題");
        builder.setMessage("內容");

        //利用 create() 方法，先將視窗建立起來但不顯示。
        dialog = builder.create();

        Button button = new Button(this);
        button.setText("顯示視窗");
        setContentView(button);

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // 利用 AlertDialog 物件的 show() 方法，顯示視窗。
                dialog.show();
            }
        });
    }
}
```
