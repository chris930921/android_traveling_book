# 使用 PagerAdapter

* MainActivity.java

```java
import android.app.Activity;
import android.os.Bundle;
import android.support.v4.view.PagerAdapter;
import android.support.v4.view.ViewPager;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;

public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        ViewPager pager = new ViewPager(this);
        pager.setId(View.generateViewId());
        // PagerAdapter 提供給一般 View 顯示在各個頁面
        pager.setAdapter(new PagerAdapter() {
            // ViewPager 會預先載入當前頁、後一頁，並保留前一頁，確保操作流暢性。
            // 除了以上三頁其他頁面都會銷毀，才不會使用太多記憶體。
            // 所以需覆寫 instantiateItem 方法，提供每一頁介面的載入方式。
            @Override
            public Object instantiateItem(ViewGroup container, int position) {
                // 建立畫面。
                TextView text = new TextView(MainActivity.this);
                text.setText("Normal Page");
                // 手動加入到參數 container 的框架中。
                container.addView(text);
                // 返回該畫面物件。
                return text;
            }
            
            // 需覆寫 destroyItem 方法，提供每一頁介面的銷毀方式，將使用的記憶體釋放。
            @Override
            public void destroyItem(ViewGroup container, int position, Object object) {
                container.removeView((View) object);
            }
            
            // 提供頁數。
            @Override
            public int getCount() {
                return 5;
            }
            
            // ViewPager 做一些狀態的改變時，為了確認其框架底下的子 View 是否是需被改變的對象，
            // 會一個一個取出現有的子 View 並和其內的 mItems 頁面陣列一個一個比對，
            // 其中會呼叫此方法來判斷子 View 是否為對應的頁面。
            // 如果覺得複雜較難理解，只需一直採用如下寫法就可以。
            @Override
            public boolean isViewFromObject(View view, Object object) {
                return view == object;
            }
        });
        setContentView(pager);
    }
}

```

* Troubleshooting

```
執行 APP 時，載入當前頁、後一頁時，執行到 instantiateItem() 時發生錯誤：
    java.lang.UnsupportedOperationException: Required method instantiateItem was not overridden
            at android.support.v4.view.PagerAdapter.instantiateItem(PagerAdapter.java:175)
---

ViewPager 判斷你沒有覆寫 instantiateItem() 的方式，就是確認你是否有執行到 super.instantiateItem();
如果方法中有撰寫 super.instantiateItem(container, position) 就會引發該錯誤。
```



* Troubleshooting

```
執行 APP 時，往後翻 ViewPager 幾頁後，往前翻頁執行到 destroyItem() 時發生錯誤：
    java.lang.UnsupportedOperationException: Required method destroyItem was not overridden
            at android.support.v4.view.PagerAdapter.destroyItem(PagerAdapter.java:192)
---

ViewPager 判斷你沒有覆寫 destroyItem() 的方式，就是確認你是否有執行到 super.destroyItem();
如果方法中有撰寫 super.destroyItem(container, position, object); 就會引發該錯誤。
```

