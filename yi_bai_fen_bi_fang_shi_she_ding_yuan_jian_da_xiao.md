# 以百分比方式設定元件大小

MainActivity.java
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        PercentRelativeLayout layout = new PercentRelativeLayout(this);
        PercentRelativeLayout.LayoutParams params = new PercentRelativeLayout.LayoutParams(
                ViewGroup.LayoutParams.WRAP_CONTENT,
                ViewGroup.LayoutParams.WRAP_CONTENT);
        
        // 高 50 %、寬 50 % 的按鈕
        PercentLayoutHelper.PercentLayoutInfo info = params.getPercentLayoutInfo();
        info.heightPercent = 0.5F;
        info.widthPercent = 0.5F;

        Button button = new Button(this);
        button.setLayoutParams(params);

        layout.addView(button);
        setContentView(layout);
    }
}
```