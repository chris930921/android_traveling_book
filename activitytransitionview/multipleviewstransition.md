# MultipleViewsTransition

```java

import android.app.Activity;
import android.app.ActivityOptions;
import android.content.Intent;
import android.os.Bundle;
import android.util.Pair;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.RelativeLayout;

public class MainActivity extends Activity {
    private static int count = 0;
    private static final String transitionName = "image";
    private static final String transitionNameTwo = "imageTwo";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 單數次開啟Activity圖會再左邊
        // 雙數次開啟Activity圖會再右邊
        int side = (count % 2 == 0) ? RelativeLayout.ALIGN_PARENT_LEFT : RelativeLayout.ALIGN_PARENT_RIGHT;

        // 建立要轉移的 view 、轉移名稱，放在上方
        final ImageView image = getImage(side, RelativeLayout.ALIGN_PARENT_TOP, transitionName);
        // 建立要轉移的 view 、轉移名稱，放在下方
        final ImageView imageTwo = getImage(side, RelativeLayout.ALIGN_PARENT_BOTTOM, transitionNameTwo);

        // 放入框架中設定介面
        final RelativeLayout container = new RelativeLayout(this);
        container.addView(image);
        container.addView(imageTwo);
        setContentView(container);

        // 按下圖片時就開啟新的 Activity，執行元件轉移動畫。
        image.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // 放入兩對要轉移的 view 和轉移名稱，都用 Pair 包起來。
                ActivityOptions options = ActivityOptions.makeSceneTransitionAnimation(
                        MainActivity.this,
                        new Pair<View, String>(image, transitionName),
                        new Pair<View, String>(imageTwo, transitionNameTwo));
                // 用雙參數的 startActivity(Intent intent, Bundle options) 方法，執行 View 轉移的動畫。
                startActivity(new Intent(MainActivity.this, MainActivity.class), options.toBundle());
            }
        });

        count++;
    }

    public ImageView getImage(int side, int gravity, String name) {
        RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(
                ViewGroup.LayoutParams.WRAP_CONTENT,
                ViewGroup.LayoutParams.WRAP_CONTENT);
        params.addRule(side);
        params.addRule(gravity);

        final ImageView v = new ImageView(this);
        v.setImageResource(R.mipmap.ic_launcher);
        v.setTransitionName(name);
        v.setLayoutParams(params);

        return v;
    }
}

```

![](Selection_303.png)
![](Selection_304.png)