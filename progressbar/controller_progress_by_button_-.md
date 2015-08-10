# 範例 - 用按鈕控制進度條增減

#### 介面
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.example.progresstest.MainActivity"
    tools:ignore="MergeRootFrame">

    <ProgressBar
        android:id="@+id/progress_bar"
        style="?android:attr/progressBarStyleHorizontal"
        android:layout_width="match_parent"
        android:layout_height="100dip"
        android:max="200"
        android:progress="50" />

    <Button
        android:id="@+id/add_one"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="第一條增加" />

    <Button
        android:id="@+id/sub_one"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="第一條減少" />

    <Button
        android:id="@+id/add_two"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="第二條增加" />

    <Button
        android:id="@+id/sub_two"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="第二條減少" />
</LinearLayout>
```

#### 程式
```java
public class MainActivity extends Activity {
    private final int MOVE = 10;

    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        final ProgressBar progressBar = (ProgressBar) findViewById(R.id.progress_bar);

        final Button addOne = (Button) findViewById(R.id.add_one);
        final Button subOne = (Button) findViewById(R.id.sub_one);
        final Button addTwo = (Button) findViewById(R.id.add_two);
        final Button subTwo = (Button) findViewById(R.id.sub_two);

        addOne.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                progressBar.incrementProgressBy(MOVE);
            }
        });
        subOne.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                progressBar.incrementProgressBy(-MOVE);
            }
        });
        addTwo.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                progressBar.incrementSecondaryProgressBy(MOVE);
            }
        });
        subTwo.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                progressBar.incrementSecondaryProgressBy(-MOVE);
            }
        });
    }
}
```
