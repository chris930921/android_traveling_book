# SingleViewTransition


```java
import android.app.Activity;
import android.app.ActivityOptions;
import android.content.Intent;
import android.os.Bundle;
import android.view.Gravity;
import android.view.View;
import android.widget.ImageView;
import android.widget.RelativeLayout;

public class MainActivity extends Activity {
    private static int count = 0;
    private static final String transitionName = "image";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 建立要轉移的view
        final ImageView image = new ImageView(this);
        image.setImageResource(R.mipmap.ic_launcher);
        // 設定轉移名稱
        image.setTransitionName(transitionName);

        final RelativeLayout container = new RelativeLayout(this);
        // 簡化程式碼，教容易貼上實作。
        // 單數次開啟Activity圖會再中間
        // 單數次開啟Activity圖會再右邊
        container.setGravity((count++ % 2 == 0) ? Gravity.CENTER : Gravity.RIGHT);
        container.addView(image);

        setContentView(container);

        // 按下圖片時就開啟新的 Activity，執行元件轉移動畫。
        image.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // 放入要轉移的 view 和轉移名稱。
                ActivityOptions options = ActivityOptions.makeSceneTransitionAnimation(MainActivity.this, image, transitionName);
                // 用雙參數的 startActivity(Intent intent, Bundle options) 方法，執行 View 轉移的動畫。
                startActivity(new Intent(MainActivity.this, MainActivity.class), options.toBundle());
            }
        });
    }
}
```